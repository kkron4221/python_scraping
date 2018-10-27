# python_scraping

#サイトからurlを取得

import urllib.request
from bs4 import BeautifulSoup


class Scraper:
    def __init__(self, site):
        self.site = site

    def scrape(self):
        r = urllib.request.urlopen(self.site)
        html = r.read()
        parser = "html.parser"
        sp = BeautifulSoup(html,parser)
        for tag in sp.find_all("a"):
            url = tag.get("href")
            if url is None:
                continue
            if "https://news.yahoo.co.jp/pickup/" in url:
                print("\n" + url)
    

news = "https://news.yahoo.co.jp/"
Scraper(news).scrape()
