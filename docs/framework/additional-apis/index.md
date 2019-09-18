---
title: 其他類別庫和 API
ms.date: 01/29/2018
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 0aed6f32bbd3ffdc9446e9d17be2d90c62444ee1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053249"
---
# <a name="additional-class-libraries-and-apis"></a>其他類別庫和 API

.NET Framework 不斷進化。 為了改善跨平臺開發並及早引進新功能，新功能會以頻外（OOB）發行。 本主題列出有提供文件的 OOB 專案。  
  
除此之外，某些程式庫會以 .NET Framework 的特定平台或實作為目標。 例如， <xref:System.Text.CodePagesEncodingProvider>類別會讓使用 .NET Framework 開發的 UWP 應用程式可以使用字碼頁編碼。 本主題也會列出這些程式庫。  
  
## <a name="oob-projects"></a>OOB 專案
  
| 專案 | 描述 |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | 提供具備執行緒安全且保證不會再變更其內容的集合。 |
| <xref:System.Net.Http.WinHttpHandler> | 提供以 Windows 的 WinHTTP 介面為基礎之 <xref:System.Net.Http.HttpClient> 的訊息處理常式。 |
| <xref:System.Numerics> | 提供可利用 SIMD 硬體加速的向量類型程式庫。| 
| <xref:System.Threading.Tasks.Dataflow> | TPL 資料流程程式庫提供資料流程元件，來協助增加啟用並行的應用程式之穩定性。 |  

## <a name="platform-specific-libraries"></a>平台特定程式庫
  
| 專案 | 描述 |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <xref:System.Text.EncodingProvider>擴充類別，讓以通用 Windows 平臺為目標的應用程式可以使用字碼頁編碼。 |  
  
## <a name="private-apis"></a>私人 API  

這些 API 支援產品基礎結構，而且不適合/不支援直接從程式碼使用。  
  
| API 名稱 |
| -------- |
| [系統 .Net. Connection 類別](connection.md) |
| [[System .net. Connection.\_m WriteList] 欄位](m_writelist.md) |
| [ConnectionGroup 類別](connectiongroup.md) |
| [[System .net. ConnectionGroup.\_m ConnectionList] 欄位](m_connectionlist.md) |
| [CoreResponseData 類別](coreresponsedata.md) |
| [[System .net. CoreResponseData.\_m ResponseHeaders] 欄位](coreresponsedata_m_responseheaders.md) |
| [[System .net. CoreResponseData\_] StatusCode 欄位](coreresponsedata_m_statuscode.md) |
| [系統 .Net. HttpWebRequest。\_AutoRedirects 欄位](_autoredirects.md) |
| [系統 .Net. HttpWebRequest。\_CoreResponse 欄位](httpwebrequest__coreresponse.md) |
| [系統 .Net. HttpWebRequest。\_HttpResponse 欄位](_httpresponse.md) |
| [[System .net. ServicePoint.\_m ConnectionGroupList] 欄位](m_connectiongrouplist.md) |
| [[System .net. ServicePointManager.\_s ServicePointTable] 欄位](s_servicepointtable.md) |
| [VisualDiagnostics. s\_isDebuggerCheckDisabledForTestPurposes 欄位](s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [System.web. DataMemberFieldEditor 類別](datamemberfieldeditor-class.md) |
| [System.web. DataMemberListEditor 類別](datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>另請參閱

- [.NET Framework 和不定期發行](../get-started/the-net-framework-and-out-of-band-releases.md)
