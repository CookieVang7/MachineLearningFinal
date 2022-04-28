# MachineLearningFinal
## Chineng "Cookie" Vang, Conner "Maurice" Hettinger, Ben Burgess

# Table of Contents
- [Overview-Purpose](#overview-purpose)
- [Solution-Structure](#solution-structure)
- [User Documentation](#user-documentation)
- [Table Structure](#table-structure)
- [About Lambda Functions](#about-lambda-functions)
    - [`GetCityData()`](#getcitydata)  
    - [`GenerateRandomRoute()`](#generaterandomroute)
    - [`GetRouteById()`](#getroutebyid)
    - [`GetBestRoutes()`](#getbestroutes)
    - [`MutateRoute()`](#mutateRoute)
- [API Details](#api-Details)
    - [`/best`](#best)
    - [`/city-data`](#city)
    - [`/mutateroute`](#mutate)
    - [`/routes`](#routes)
    - [`/routes/{routeId}`](#getRoute)
- [IAM Roles](#iam-roles)
- [Leaflet Details](#leaflet-details)
- [Appendix I (Lambda function code)](#appendix-i-lambda-function-code)
    - [`GetCityData()`](#getcitydata-1)
    - [`GenerateRandomRoute()`](#generaterandomroute-1)
    - [`GetBestRoutes()`](#getbestroutes-1)
    - [`GetRouteById()`](#getroutebyid-1)
    - [`MutateRoute()`](#mutateroute-1)
- [Appendix II (JavaScript file)](#appendix-ii-javascript-file)
- [Appendix III (HTML file)](#appendix-iii-html-file)

## Overview-Purpose
This project tackles the Traveling Salesman Problem (TSP) by evolving TSP routes. The Traveling Salesman Problem inquires that if you are given a list of cities and their distances from one another, what is the shortest possible route that visits each city including looping back to the beginning city? An answer to this can be accomplished by taking an initial population of routes between all the cities and evolving the best of them (called parent routes) to create shorter routes (called child routes). The process is then repeated with the new set of child routes. Each iteration of the process is called a generation where the number of generations is specified by the user.
