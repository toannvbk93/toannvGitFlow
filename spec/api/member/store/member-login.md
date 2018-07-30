# member/login

## Overview

| Endpoint | Name | Type |
| --- | --- | --- |
| /member/login | login | GET |

Authentication

## Specification

### Request

tmid, token as Post parameters

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| tmid | String! | - | TMID\(nonce key\) |
| token | String! | - | Request Token of TSUTAYA API |

### Response

Redirect to “/member”

#### Error

TBD

