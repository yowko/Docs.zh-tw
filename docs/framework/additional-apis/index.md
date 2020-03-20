---
title: 其他類別庫和 API
ms.date: 11/19/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: abf7fd20988ebaaaf1a40ccc168c636fd0dacc1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155904"
---
# <a name="additional-class-libraries-and-apis"></a>其他類別庫和 API

.NET 框架在不斷發展。 為了改進跨平臺開發並儘早引入新功能，新功能將發佈在頻段 （OOB） 外。 本主題列出有提供文件的 OOB 專案。  
  
除此之外，某些程式庫會以 .NET Framework 的特定平台或實作為目標。 例如，<xref:System.Text.CodePagesEncodingProvider>類使字碼頁編碼可用於使用 .NET 框架開發的 UWP 應用。 本主題也會列出這些程式庫。  
  
## <a name="oob-projects"></a>OOB 專案
  
| 隨附此逐步解說的專案 | 描述 |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | 提供具備執行緒安全且保證不會再變更其內容的集合。 |
| <xref:System.Net.Http.WinHttpHandler> | 提供以 Windows 的 WinHTTP 介面為基礎之 <xref:System.Net.Http.HttpClient> 的訊息處理常式。 |
| <xref:System.Numerics> | 提供可利用 SIMD 硬體加速的向量類型程式庫。|
| <xref:System.Threading.Tasks.Dataflow> | TPL 資料流程程式庫提供資料流程元件，來協助增加啟用並行的應用程式之穩定性。 |  

## <a name="platform-specific-libraries"></a>平台特定程式庫
  
| 隨附此逐步解說的專案 | 描述 |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | 擴展類<xref:System.Text.EncodingProvider>，使字碼頁編碼可用於面向通用 Windows 平臺的應用。 |  
  
## <a name="private-apis"></a>私人 API  

這些 API 支援產品基礎結構，而且不適合/不支援直接從程式碼使用。  
  
* [微軟.SqlServer.Server.Smiorder屬性.專案屬性](microsoft.sqlserver.server.smiorderproperty.item.md)
* [系統.例外.準備重新移動方法](system.exception.prepforremoting.md)
* [系統.資料.SqlTypes.SqlChars.流屬性](system.data.sqltypes.sqlchars.stream.md)
* [系統.資料.SqlTypes.SqlStreamChars建構函式](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [系統.資料.SqlTypes.SqlStreamChars.CanSeek 屬性](system.data.sqltypes.sqlstreamchars.canseek.md)
* [系統.資料.SqlTypes.SqlStreamChars.IsNull 屬性](system.data.sqltypes.sqlstreamchars.isnull.md)
* [系統.資料.SqlTypes.SqlStreamChars.長度屬性](system.data.sqltypes.sqlstreamchars.length.md)
* [系統.資料.SqlTypes.SqlStreamChars.關閉方法](system.data.sqltypes.sqlstreamchars.close.md)
* [系統.資料.SqlTypes.SqlStreamChars.Dispose 方法](system.data.sqltypes.sqlstreamchars.dispose.md)
* [系統.資料.SqlTypes.SqlStreamChars.Flush 方法](system.data.sqltypes.sqlstreamchars.flush.md)
* [系統.資料.SqlTypes.SqlStreamChars.讀取方法](system.data.sqltypes.sqlstreamchars.read.md)
* [系統.資料.SqlTypes.SqlStreamChars.查找方法](system.data.sqltypes.sqlstreamchars.seek.md)
* [系統.資料.SqlTypes.SqlStreamChars.set 長度方法](system.data.sqltypes.sqlstreamchars.setlength.md)
* [系統.資料.SqlTypes.SqlStreamChars.寫入方法](system.data.sqltypes.sqlstreamchars.write.md)
* [系統.IO.記憶體流.內部獲取源和長度方法](system.io.memorystream.internalgetoriginandlength.md)
* [系統.Net.連接類](connection.md)
* [系統.Net.連接.m\_寫入清單欄位](m_writelist.md)
* [系統.Net.連接組類](connectiongroup.md)
* [系統.Net.連接組.m\_連接清單欄位](m_connectionlist.md)
* [系統.Net.連接流.連接屬性](system.net.connectstream.connection.md)
* [系統.Net.核心回應資料類](coreresponsedata.md)
* [系統.Net.核心回應資料.m\_回應標題欄位](coreresponsedata_m_responseheaders.md)
* [系統.Net.核心回應資料.m\_狀態碼欄位](coreresponsedata_m_statuscode.md)
* [系統.Net.HttpWeb請求。\_自動重定向欄位](_autoredirects.md)
* [系統.Net.HttpWeb請求。\_核心回應欄位](httpwebrequest__coreresponse.md)
* [系統.Net.HttpWeb請求。\_Http 回應欄位](_httpresponse.md)
* [系統.Net.池流.網路流屬性](system.net.pooledstream.networkstream.md)
* [系統.Net.RtcState 類](system.net.rtcstate.md)
* [系統.Net.服務點.m\_連接組清單欄位](m_connectiongrouplist.md)
* [系統.Net.服務點管理器.的服務\_點表字段](s_servicepointtable.md)
* [系統.Net.TlsStream.m_Worker欄位](system.net.tlsstream.m_worker.md)
* [系統.Net.Security.SslState.Ssl協定屬性](system.net.security.sslstate.sslprotocol.md)
* [系統.服務模式.通道.消息.正文string方法](system.servicemodel.channels.message.bodytostring.md)
* [系統.服務模式.通道.消息.編寫開始標題方法](system.servicemodel.channels.message.writestartheaders.md)
* [系統.Windows.診斷.視覺診斷是\_調試器檢查禁用的"測試目的"欄位](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [系統.Windows.表單.設計.資料成員欄位編輯器類](datamemberfieldeditor-class.md)
* [系統.Windows.表單.設計.資料成員清單編輯器類](datamemberlisteditor-class.md)
* [系統.Xml.XmlReader.createSqlReader方法](system.xml.xmlreader.createsqlreader.md)
* [阿多德布連接介面](adodb.connection.md)
* [阿多德布事件原因枚舉](adodb.eventreasonenum.md)
* [阿多德布事件狀態枚舉](adodb.eventstatusenum.md)
* [stdole。DISPPARAMS 結構](stdole.dispparams.md)
* [stdole。EXCEPINFO 結構](stdole.excepinfo.md)
* [stdole。IFont.Name酒店](stdole.ifont.name.md)
* [stdole。IFontDisp 介面](stdole.ifontdisp.md)
* [stdole。IPicture.Handle 屬性](stdole.ipicture.handle.md)
* [stdole。IPictureDisp.Handle 屬性](stdole.ipicturedisp.handle.md)
* [stdole。斯特芬介面](stdole.stdfont.md)
* [stdole。StdPicture 介面](stdole.stdpicture.md)
  
## <a name="see-also"></a>另請參閱

* [.NET Framework 和不定期發行](../get-started/the-net-framework-and-out-of-band-releases.md)
