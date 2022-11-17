---
title: URLSession
categories: Foundation
description: URLSession
---

# URLSession

iOS 支持 Multipath TCP (MPTCP)，并且允许 iPhone 或 iPad 通过蜂窝移动数据连接建立与目标主机的备份 TCP 连接。
网络管理员可能需要使用 MPTCP。使用标准家庭网络的客户无需启用 MPTCP。
关于 Multipath TCP
MPTCP 是对传输控制协议 (TCP) 规范的一组扩展。凭借 MPTCP，客户端可以通过不同网络适配器连接到有多个连接的同一目标主机。这可在各主机间建立强大而高效的数据连接，并且与现有的网络基础设施兼容。 

```swift
enum MultipathServiceType : Int
```

NSURLError 错误码

```
NSURLErrorUnknown = -1,
NSURLErrorCancelled = -999,
NSURLErrorBadURL = -1000,
NSURLErrorTimedOut = -1001,
NSURLErrorUnsupportedURL = -1002,
NSURLErrorCannotFindHost = -1003,
NSURLErrorCannotConnectToHost = -1004,
NSURLErrorNetworkConnectionLost = -1005,
NSURLErrorDNSLookupFailed = -1006,
NSURLErrorHTTPTooManyRedirects = -1007,
NSURLErrorResourceUnavailable = -1008,
NSURLErrorNotConnectedToInternet = -1009,
NSURLErrorRedirectToNonExistentLocation = -1010,
NSURLErrorBadServerResponse = -1011,
NSURLErrorUserCancelledAuthentication = -1012,
NSURLErrorUserAuthenticationRequired = -1013,
NSURLErrorZeroByteResource = -1014,
NSURLErrorCannotDecodeRawData = -1015,
NSURLErrorCannotDecodeContentData = -1016,
NSURLErrorCannotParseResponse = -1017,
NSURLErrorAppTransportSecurityRequiresSecureConnection = -1022,
NSURLErrorFileDoesNotExist = -1100,
NSURLErrorFileIsDirectory = -1101,
NSURLErrorNoPermissionsToReadFile = -1102,
NSURLErrorDataLengthExceedsMaximum = -1103,
NSURLErrorSecureConnectionFailed = -1200,
NSURLErrorServerCertificateHasBadDate = -1201,
NSURLErrorServerCertificateUntrusted = -1202,
NSURLErrorServerCertificateHasUnknownRoot = -1203,
NSURLErrorServerCertificateNotYetValid = -1204,/Users/wang/Downloads/非完整下载全log 2/Unisdk_log/download_result_1644903266.txt
/Users/wang/Desktop/Downfiles/downfiles.txt
NSURLErrorClientCertificateRejected = -1205,
NSURLErrorClientCertificateRequired = -1206,
NSURLErrorCannotLoadFromNetwork = -2000,
NSURLErrorCannotCreateFile = -3000,
NSURLErrorCannotOpenFile = -3001,
NSURLErrorCannotCloseFile = -3002,
NSURLErrorCannotWriteToFile = -3003,
NSURLErrorCannotRemoveFile = -3004,
NSURLErrorCannotMoveFile = -3005,
NSURLErrorDownloadDecodingFailedMidStream = -3006,
NSURLErrorDownloadDecodingFailedToComplete = -3007,
NSURLErrorInternationalRoamingOff = -1018,
NSURLErrorCallIsActive = -1019,
NSURLErrorDataNotAllowed = -1020,
NSURLErrorRequestBodyStreamExhausted = -1021,
NSURLErrorBackgroundSessionRequiresSharedContainer = -995,
NSURLErrorBackgroundSessionInUseByAnotherProcess = -996,
NSURLErrorBackgroundSessionWasDisconnected = -997
```

https://support.apple.com/zh-cn/HT201373