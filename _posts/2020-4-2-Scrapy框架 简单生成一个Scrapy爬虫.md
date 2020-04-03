---
layout: post
title: Scrapy框架 简单生成一个Scrapy爬虫
date: 2020-4-2
Author: Ain
tags: [Study, Python, Spider]
comments: true
---



1. ###### 创建一个Scrapy项目

   - scrapy startproject myspider[工程名]
   - cd myspider    #进入到工程文件夹 

2. 生成一个爬虫

   - scrapy genspider myspider_name spider.com

3. 配置好爬虫后，在爬虫工程文件夹下启动

   - scrapy crawl spider_name
