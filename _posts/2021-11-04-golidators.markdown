---
layout: post
title:  "golidators"
date:   2021-11-04 10:26:23 +0300
categories: projects
tags: go golang validation data-validation validator validations validate data-validator golang-package golidators
---
![Workflow](https://github.com/eredotpkfr/golidators/actions/workflows/go.yml/badge.svg) ![Go Report Card](https://goreportcard.com/badge/github.com/eredotpkfr/golidators) ![Go Reference](https://pkg.go.dev/badge/github.com/eredotpkfr/golidators.svg) ![Go Version](https://img.shields.io/github/go-mod/go-version/eredotpkfr/golidators) ![Release](https://img.shields.io/github/v/release/eredotpkfr/golidators) ![License](https://img.shields.io/badge/license-MIT-blue) ![Stars](https://img.shields.io/github/stars/eredotpkfr/golidators?style=social)

# golidators
Golidators is a golang package, it includes basic data validation functions and regexes.

## Install
{% highlight bash linenos %}
$ go get github.com/eredotpkfr/golidators
{% endhighlight %}

## Overview
Following validators available on this package:
- Domain
- MD5, SHA1, SHA224, SHA256, SHA512
- IPv4, IPv4CIDR, IPv6, IPv6CIDR
- MAC
- Port
- URL
- UUID

## Usage
Just import and use it. Also see documentation at [pkg.go.dev](https://pkg.go.dev/github.com/eredotpkfr/golidators#section-documentation)
{% highlight go linenos %}
package main

import (
    "github.com/eredotpkfr/golidators"
    "fmt"
)

func main() {
  fmt.Println(golidators.Domain("www.example.com"))
  // true
  fmt.Println(golidators.Ipv4("::1"))
  // false
  fmt.Println(golidators.Ipv6("::1"))
  // true
  fmt.Println(golidators.Url("https://www.example.com"))
  // true
  fmt.Println(golidators.Ipv4Cidr("127.0.0.1/12"))
  // true
  fmt.Println(golidators.Md5("foo/bar"))
  // false
}
{% endhighlight %}

## Contact
Blog - [erdoganyoksul.com](https://www.erdoganyoksul.com)
Mail - erdoganyoksul3@gmail.com

