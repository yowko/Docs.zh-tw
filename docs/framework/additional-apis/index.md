---
title: 其他類別庫和 API
ms.date: 11/19/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: e1e2af584c73b1c0b2548cdd3fcbd8517dfa330d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429333"
---
# <a name="additional-class-libraries-and-apis"></a>其他類別庫和 API

The .NET Framework is constantly evolving. To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB). 本主題列出有提供文件的 OOB 專案。  
  
除此之外，某些程式庫會以 .NET Framework 的特定平台或實作為目標。 For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework. 本主題也會列出這些程式庫。  
  
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
| <xref:System.Text.CodePagesEncodingProvider> | Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform. |  
  
## <a name="private-apis"></a>私人 API  

這些 API 支援產品基礎結構，而且不適合/不支援直接從程式碼使用。  
  
* [Microsoft.SqlServer.Server.SmiOrderProperty.Item Property](microsoft.sqlserver.server.smiorderproperty.item.md)
* [System.Exception.PrepForRemoting Method](system.exception.prepforremoting.md)
* [System.Data.SqlTypes.SqlChars.Stream Property](system.data.sqltypes.sqlchars.stream.md)
* [System.Data.SqlTypes.SqlStreamChars Constructor](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [System.Data.SqlTypes.SqlStreamChars.CanSeek Property](system.data.sqltypes.sqlstreamchars.canseek.md)
* [System.Data.SqlTypes.SqlStreamChars.IsNull Property](system.data.sqltypes.sqlstreamchars.isnull.md)
* [System.Data.SqlTypes.SqlStreamChars.Length Property](system.data.sqltypes.sqlstreamchars.length.md)
* [System.Data.SqlTypes.SqlStreamChars.Close Method](system.data.sqltypes.sqlstreamchars.close.md)
* [System.Data.SqlTypes.SqlStreamChars.Dispose Method](system.data.sqltypes.sqlstreamchars.dispose.md)
* [System.Data.SqlTypes.SqlStreamChars.Flush Method](system.data.sqltypes.sqlstreamchars.flush.md)
* [System.Data.SqlTypes.SqlStreamChars.Read Method](system.data.sqltypes.sqlstreamchars.read.md)
* [System.Data.SqlTypes.SqlStreamChars.Seek Method](system.data.sqltypes.sqlstreamchars.seek.md)
* [System.Data.SqlTypes.SqlStreamChars.SetLength Method](system.data.sqltypes.sqlstreamchars.setlength.md)
* [System.Data.SqlTypes.SqlStreamChars.Write Method](system.data.sqltypes.sqlstreamchars.write.md)
* [System.IO.MemoryStream.InternalGetOriginAndLength Method](system.io.memorystream.internalgetoriginandlength.md)
* [System.Net.Connection Class](connection.md)
* [System.Net.Connection.m\_WriteList Field](m_writelist.md)
* [System.Net.ConnectionGroup Class](connectiongroup.md)
* [System.Net.ConnectionGroup.m\_ConnectionList Field](m_connectionlist.md)
* [System.Net.ConnectStream.Connection Property](system.net.connectstream.connection.md)
* [System.Net.CoreResponseData Class](coreresponsedata.md)
* [System.Net.CoreResponseData.m\_ResponseHeaders Field](coreresponsedata_m_responseheaders.md)
* [System.Net.CoreResponseData.m\_StatusCode Field](coreresponsedata_m_statuscode.md)
* [System.Net.HttpWebRequest.\_AutoRedirects Field](_autoredirects.md)
* [System.Net.HttpWebRequest.\_CoreResponse Field](httpwebrequest__coreresponse.md)
* [System.Net.HttpWebRequest.\_HttpResponse Field](_httpresponse.md)
* [System.Net.PooledStream.NetworkStream Property](system.net.pooledstream.networkstream.md)
* [System.Net.RtcState class](system.net.rtcstate.md)
* [System.Net.ServicePoint.m\_ConnectionGroupList Field](m_connectiongrouplist.md)
* [System.Net.ServicePointManager.s\_ServicePointTable Field](s_servicepointtable.md)
* [System.Net.TlsStream.m_Worker Field](system.net.tlsstream.m_worker.md)
* [System.Net.Security.SslState.SslProtocol Property](system.net.security.sslstate.sslprotocol.md)
* [System.ServiceModel.Channels.Message.BodyToString Method](system.servicemodel.channels.message.bodytostring.md)
* [System.ServiceModel.Channels.Message.WriteStartHeaders Method](system.servicemodel.channels.message.writestartheaders.md)
* [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [System.Windows.Forms.Design.DataMemberFieldEditor Class](datamemberfieldeditor-class.md)
* [System.Windows.Forms.Design.DataMemberListEditor Class](datamemberlisteditor-class.md)
* [System.Xml.XmlReader.CreateSqlReader Method](system.xml.xmlreader.createsqlreader.md)
* [adodb.Connection Interface](adodb.connection.md)
* [adodb.EventReason Enum](adodb.eventreasonenum.md)
* [adodb.EventStatus Enum](adodb.eventstatusenum.md)
* [stdole.DISPPARAMS Structure](stdole.dispparams.md)
* [stdole.EXCEPINFO Structure](stdole.excepinfo.md)
* [stdole.IFont.Name Property](stdole.ifont.name.md)
* [stdole.IFontDisp Interface](stdole.ifontdisp.md)
* [stdole.IPicture.Handle Property](stdole.ipicture.handle.md)
* [stdole.IPictureDisp.Handle Property](stdole.ipicturedisp.handle.md)
* [stdole.StdFont Interface](stdole.stdfont.md)
* [stdole.StdPicture Interface](stdole.stdpicture.md)
  
## <a name="see-also"></a>請參閱

* [.NET Framework 和不定期發行](../get-started/the-net-framework-and-out-of-band-releases.md)
