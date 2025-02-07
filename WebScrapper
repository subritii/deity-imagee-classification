import os
import requests
from bs4 import BeautifulSoup
from urllib.parse import urljoin, urlparse

# Function to download images
def download_image(image_url, folder_path):
    file_name = os.path.basename(urlparse(image_url).path)
    response = requests.get(image_url, stream=True)
    if response.status_code == 200:
        file_path = os.path.join(folder_path, file_name)
        with open(file_path, 'wb') as f:
            f.write(response.content)
        print(f"Image downloaded: {file_path}")
    else:
        print(f"Failed to download image: {image_url}")

# Function to scrape and download images from the visited pages
def scrape_images_from_url(url, folder_path='images'):
    if not os.path.exists(folder_path):
        os.makedirs(folder_path)

    response = requests.get(url)
    soup = BeautifulSoup(response.content, 'html.parser')

    # Find all <a> tags that contain links to individual image pages
    for a_tag in soup.find_all('a', href=True):
        image_page_url = urljoin(url, a_tag['href'])
        
        # Visit each image page and scrape the full-size image
        try:
            image_page_response = requests.get(image_page_url)
            image_page_soup = BeautifulSoup(image_page_response.content, 'html.parser')

            # Find full-size image (usually in <img> tag)
            full_image_tag = image_page_soup.find('img')
            if full_image_tag and 'src' in full_image_tag.attrs:
                full_image_url = urljoin(image_page_url, full_image_tag['src'])
                # Download the full-size image
                download_image(full_image_url, folder_path)

        except Exception as e:
            print(f"Error visiting {image_page_url}: {e}")

# Example usage
if __name__ == "__main__":
    url_to_scrape = 'https://www.himalayanart.org/search/search_results.cfm?useListView=0&figureCategoryID=110&figureID=718&collectionID=ANY&mandala=ANY&repousse=ANY&lineage=any&originID=any&backgroundColor=&creationDate=ANY&materialID=ANY&searchObjectType=all&page=4'
    scrape_images_from_url(url_to_scrape)
