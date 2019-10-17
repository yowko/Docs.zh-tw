---
title: 其他類別庫和 API
ms.date: 10/09/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: b869ca2f5e17db9a204a8b757b5e24ebb209d7c5
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395653"
---
# <a name="additional-class-libraries-and-apis"></a>其他類別庫和 API

.NET Framework 不斷進化。 為了改善跨平臺開發並及早引進新功能，新功能會以頻外（OOB）發行。 本主題列出有提供文件的 OOB 專案。  
  
除此之外，某些程式庫會以 .NET Framework 的特定平台或實作為目標。 例如，@no__t 0 類別可以讓使用 .NET Framework 開發的 UWP 應用程式使用字碼頁編碼。 本主題也會列出這些程式庫。  
  
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
| <xref:System.Text.CodePagesEncodingProvider> | 擴充 @no__t 0 類別，讓以通用 Windows 平臺為目標的應用程式可以使用字碼頁編碼。 |  
  
## <a name="private-apis"></a>私人 API  

這些 API 支援產品基礎結構，而且不適合/不支援直接從程式碼使用。  
  
* [SmiOrderProperty. Item 屬性](microsoft.sqlserver.server.smiorderproperty.item.md)
* [PrepForRemoting 方法](system.exception.prepforremoting.md)
* [SqlTypes. SqlChars 資料流程屬性](system.data.sqltypes.sqlchars.stream.md)
* [SqlTypes. SqlStreamChars 函數](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [SqlTypes. SqlStreamChars. CanSeek 屬性](system.data.sqltypes.sqlstreamchars.canseek.md)
* [SqlTypes. SqlStreamChars. IsNull 屬性](system.data.sqltypes.sqlstreamchars.isnull.md)
* [SqlTypes. SqlStreamChars. Length 屬性](system.data.sqltypes.sqlstreamchars.length.md)
* [SqlTypes. SqlStreamChars. Close 方法](system.data.sqltypes.sqlstreamchars.close.md)
* [SqlTypes. SqlStreamChars. Dispose 方法](system.data.sqltypes.sqlstreamchars.dispose.md)
* [SqlTypes. SqlStreamChars. Flush 方法](system.data.sqltypes.sqlstreamchars.flush.md)
* [SqlTypes. SqlStreamChars. Read 方法](system.data.sqltypes.sqlstreamchars.read.md)
* [SqlTypes. SqlStreamChars. Seek 方法](system.data.sqltypes.sqlstreamchars.seek.md)
* [SqlTypes. SqlStreamChars. SetLength 方法](system.data.sqltypes.sqlstreamchars.setlength.md)
* [SqlTypes. SqlStreamChars. Write 方法](system.data.sqltypes.sqlstreamchars.write.md)
* [系統 .Net. Connection 類別](connection.md)
* [[系統 .Net]。 m @ no__t-1WriteList 欄位](m_writelist.md)
* [ConnectionGroup 類別](connectiongroup.md)
* [ConnectionGroup. m @ no__t-1ConnectionList 欄位](m_connectionlist.md)
* [CoreResponseData 類別](coreresponsedata.md)
* [CoreResponseData. m @ no__t-1ResponseHeaders 欄位](coreresponsedata_m_responseheaders.md)
* [CoreResponseData. m @ no__t-1StatusCode 欄位](coreresponsedata_m_statuscode.md)
* [HttpWebRequest. \_AutoRedirects 欄位](_autoredirects.md)
* [HttpWebRequest. \_CoreResponse 欄位](httpwebrequest__coreresponse.md)
* [HttpWebRequest. \_HttpResponse 欄位](_httpresponse.md)
* [ServicePoint. m @ no__t-1ConnectionGroupList 欄位](m_connectiongrouplist.md)
* [System .Net. ServicePointManager. s @ no__t-1ServicePointTable 欄位](s_servicepointtable.md)
* [VisualDiagnostics. s @ no__t-1isDebuggerCheckDisabledForTestPurposes 欄位](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [System.web. DataMemberFieldEditor 類別](datamemberfieldeditor-class.md)
* [System.web. DataMemberListEditor 類別](datamemberlisteditor-class.md)
* [adodb.連接介面](adodb.connection.md)
* [adodb.EventReason 列舉](adodb.eventreasonenum.md)
* [adodb.EventStatus 列舉](adodb.eventstatusenum.md)
* [stdole.DISPPARAMS 結構](stdole.dispparams.md)
* [stdole.EXCEPINFO 結構](stdole.excepinfo.md)
* [stdole.IFont.Name 屬性](stdole.ifont.name.md)
* [stdole.IFontDisp 介面](stdole.ifontdisp.md)
* [stdole.圖片屬性](stdole.ipicture.handle.md)
* [stdole.IPictureDisp 屬性](stdole.ipicturedisp.handle.md)
* [stdole.StdFont 介面](stdole.stdfont.md)
* [stdole.StdPicture 介面](stdole.stdpicture.md)
  
## <a name="see-also"></a>請參閱

* [.NET Framework 和不定期發行](../get-started/the-net-framework-and-out-of-band-releases.md)
