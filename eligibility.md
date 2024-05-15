
# Pirum Eligibility checker

In order to fulfill a need expressed by many clients, Pirum has decided to offer a new set of APIs to its clients. The purpose of these APIs is to observe how their eligibility schedules define if and how much of a particular asset can be allocated to one of their bank accounts.

A new team has been assembled to execute the delivery of the project and it is your job to help them reach a successful outcome.

## Terminology:

* eligibility schedule: a collection of rules, usually defined as predicates over an asset and possibly a bank account, that identify if a particular asset can be allocated to a bank account, and how much of it. For the purposes of this test, we will only consider the following simplified model:

  - eligibility rules: these are the rules that determine if yes or no an asset can be allocated to an account
  - limit rules: these are the rules that determine how much of an asset can be allocated to an account
  - in both cases, *all* rules must be respected for an asset/account combination to work out

* asset: for the purposes of this test, we will only consider an asset to be either cash in a particular denomination, or shares of a particular publicly traded company

* account: a bank account at a particular bank

## Requirements:

Functionally, the APIs that we propose to offer are the following:

* POST /schedules: an API to upload an eligibility schedule

* GET /schedules/{scheduleId}: an API to get the details of an eligibility schedule

* GET /schedules/{scheduleId}/check?accountId={accountId}&assetBundleId={assetBundleId}: an API to find out which assets in a bundle can be allocated to an account according to that schedule

* DELETE /schedules/{scheduleId}: an API to remove an existing schedule

* POST /assets: an API to upload assets, creating a new asset bundle

* GET /assets/{assetBundleId}: an API to get the assets in a bundle

* DELETE /assets/{assetBundleId}: an API to delete a bundle of assets

* POST /accounts: an API to create a account record

* GET /accounts/{accountId}: an API to get the account details

* DELETE /accounts/{accountId}: an API to delete an account

In addition to the APIs above, it has been decided to expose additional endpoints to observe the internal state of the service:

* GET /admin/health: an API endpoint that yield a yes/no answer depending on whether the system is healthy

* GET /admin/status: an API endpint that yields important information about the health of the system:

  * how many requests per second it is receiving
  * what the latency looks like
  * how many successful responses
  * how many 4xx responses
  * how many 5xx responses

## Questions

As part of this test, we want you to think as an engineering manager and explain how you will ensure the successful delivery of the service.

For instance, and this is not an exhaustive list, how will you address the following points:

* overall project roadmap: clients expect a delivery within 6 months as they are currently building their own internal service that will use this API

* getting data out of stakeholders (clients, 3rd parties, POs, etc.): eligibility schedules, assets and accounts have many properties that need to be understand for the team to write a correct implementation of the checking process

* team workflow: how best can the team make use of its time

* tech debt: what is a good strategy to either avoid or manage tech debt over time

* developer well-being: how can the team flourish and stay positive even in the advent of unexpected delays/issues
