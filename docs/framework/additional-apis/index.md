---
title: 其他類別庫和 API
description: 探索 .NET 中的其他類別庫和 Api，包括頻外 (OOB) 專案、平臺特定程式庫和私用 Api。
ms.date: 08/11/2020
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: 55cb37cc2c9184eeb55ee0aab39e97f4a3f7b7d8
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877635"
---
# <a name="additional-class-libraries-and-apis"></a>其他類別庫和 API

本文列出的 .NET Framework Api 是以頻外方式發行、以特定平臺為目標，或為私用或內部類型。

## <a name="oob-projects"></a>OOB 專案

為了改進跨平臺開發，並及早引進新功能，部分 .NET Framework 功能已在頻外 (OOB) 中發行。

| 專案 | 描述 |
| ------- | ----------- |
| <xref:System.Collections.Immutable> | 提供具備執行緒安全且保證不會再變更其內容的集合。 |
| <xref:System.Net.Http.WinHttpHandler> | 提供以 Windows 的 WinHTTP 介面為基礎之 <xref:System.Net.Http.HttpClient> 的訊息處理常式。 |
| <xref:System.Numerics> | 提供可利用 SIMD 硬體加速的向量類型程式庫。|
| <xref:System.Threading.Tasks.Dataflow> | TPL 資料流程程式庫提供資料流程元件，來協助增加啟用並行的應用程式之穩定性。 |

## <a name="platform-specific-libraries"></a>平台特定程式庫

某些程式庫以特定平臺為目標。 例如，類別可 <xref:System.Text.CodePagesEncodingProvider> 讓使用 .NET Framework 開發的 UWP 應用程式使用字碼頁編碼。

| 專案 | 描述 |
| ------- | ----------- |
| <xref:System.Text.CodePagesEncodingProvider> | 擴充 <xref:System.Text.EncodingProvider> 類別，讓目標為通用 Windows 平臺的應用程式可以使用字碼頁編碼。 |

## <a name="private-apis"></a>私人 API

這些 Api 支援產品基礎結構，而且不適合直接從程式碼使用或支援。

* [SmiOrderProperty。 Item 屬性](microsoft.sqlserver.server.smiorderproperty.item.md)
* [Exception.prepforremoting 方法](system.exception.prepforremoting.md)
* [SqlTypes. SqlChars 資料流程屬性](system.data.sqltypes.sqlchars.stream.md)
* [SqlTypes. SqlStreamChars 函數](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [SqlTypes. SqlStreamChars. CanSeek 屬性](system.data.sqltypes.sqlstreamchars.canseek.md)
* [SqlTypes. SqlStreamChars. IsNull 屬性](system.data.sqltypes.sqlstreamchars.isnull.md)
* [SqlTypes. SqlStreamChars. Length 屬性](system.data.sqltypes.sqlstreamchars.length.md)
* [SqlTypes. SqlStreamChars. Close 方法](system.data.sqltypes.sqlstreamchars.close.md)
* [SqlTypes. SqlStreamChars Dispose 方法](system.data.sqltypes.sqlstreamchars.dispose.md)
* [SqlTypes. SqlStreamChars. Flush 方法](system.data.sqltypes.sqlstreamchars.flush.md)
* [SqlTypes. SqlStreamChars. Read 方法](system.data.sqltypes.sqlstreamchars.read.md)
* [SqlTypes. SqlStreamChars. Seek 方法](system.data.sqltypes.sqlstreamchars.seek.md)
* [SqlTypes. SqlStreamChars. SetLength 方法](system.data.sqltypes.sqlstreamchars.setlength.md)
* [SqlTypes. SqlStreamChars. Write 方法](system.data.sqltypes.sqlstreamchars.write.md)
* [MemoryStream. InternalGetOriginAndLength 方法](system.io.memorystream.internalgetoriginandlength.md)
* [System ComNetOS 類別](system.net.comnetos.md)
* [System .Net. Connection 類別](connection.md)
* [System .Net. \_ WriteList 欄位](m_writelist.md)
* [System ConnectionGroup 類別](connectiongroup.md)
* [ConnectionGroup. m \_ ConnectionList 欄位](m_connectionlist.md)
* [ConnectStream 連接屬性](system.net.connectstream.connection.md)
* [System CoreResponseData 類別](coreresponsedata.md)
* [CoreResponseData. m \_ ResponseHeaders 欄位](coreresponsedata_m_responseheaders.md)
* [[CoreResponseData] \_ StatusCode 欄位](coreresponsedata_m_statuscode.md)
* [System ExceptionHelper 類別](system.net.exceptionhelper.md)
* [System HttpStatusDescription 類別](system.net.httpstatusdescription.md)
* [系統 HttpWebRequest。 \_AutoRedirects 欄位](_autoredirects.md)
* [系統 HttpWebRequest。 \_CoreResponse 欄位](httpwebrequest__coreresponse.md)
* [系統 HttpWebRequest。 \_HttpResponse 欄位](_httpresponse.md)
* [System .Net. 記錄類別](system.net.logging.md)
* [System MailAddressParser 類別](system.net.mail.mailaddressparser.md)
* [System QuotedPairReader 類別](system.net.mail.quotedpairreader.md)
* [MailBnfHelper 類別](system.net.mime.mailbnfhelper.md)
* [PooledStream. NetworkStream 屬性](system.net.pooledstream.networkstream.md)
* [System RtcState 類別](system.net.rtcstate.md)
* [SslState. SslProtocol 屬性](system.net.security.sslstate.sslprotocol.md)
* [>servicepoint. m \_ ConnectionGroupList 欄位](m_connectiongrouplist.md)
* [ServicePointManager. CloseConnectionGroups 方法](system.net.servicepointmanager.closeconnectiongroups.md)
* [[系統 ServicePointManager] \_ ServicePointTable 欄位](s_servicepointtable.md)
* [System.Net.TlsStream.m_Worker 欄位](system.net.tlsstream.m_worker.md)
* [System UnsafeNclNativeMethods 類別](system.net.unsafenclnativemethods.md)
* [有設定 webheadercollection. AddInternal 方法](system.net.webheadercollection.addinternal.md)
* [System.servicemodel. BodyToString 方法](system.servicemodel.channels.message.bodytostring.md)
* [System.servicemodel. WriteStartHeaders 方法](system.servicemodel.channels.message.writestartheaders.md)
* [ControlBuilderInterceptor 類別。](controlbuilderinterceptor-class.md)
* [GridViewHeaderRowPresenter. FindHeaderByColumn 方法](system.windows.controls.gridviewheaderrowpresenter.findheaderbycolumn.md)
* [GridViewHeaderRowPresenter. MakeParentItemsControlGotFocus 方法](system.windows.controls.gridviewheaderrowpresenter.makeparentitemscontrolgotfocus.md)
* [GridViewHeaderRowPresenter. PrepareHeaderDrag 方法](system.windows.controls.gridviewheaderrowpresenter.prepareheaderdrag.md)
* [VisualDiagnostics. s \_ isDebuggerCheckDisabledForTestPurposes 欄位](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [System.string. DataMemberFieldEditor 類別](datamemberfieldeditor-class.md)
* [System.string. DataMemberListEditor 類別](datamemberlisteditor-class.md)
* [System.Xml.XmlXmlreader.createsqlreader 方法](system.xml.xmlreader.createsqlreader.md)
* [adodb.連接介面](adodb.connection.md)
* [adodb.EventReason 列舉](adodb.eventreasonenum.md)
* [adodb.EventStatus 列舉](adodb.eventstatusenum.md)
* [stdole.DISPPARAMS 結構](stdole.dispparams.md)
* [stdole.EXCEPINFO 結構](stdole.excepinfo.md)
* [stdole.IFont.Name 屬性](stdole.ifont.name.md)
* [stdole.>ifontdisp 介面](stdole.ifontdisp.md)
* [stdole.圖片。控制碼屬性](stdole.ipicture.handle.md)
* [stdole.IPictureDisp。控制碼屬性](stdole.ipicturedisp.handle.md)
* [stdole.StdFont 介面](stdole.stdfont.md)
* [stdole.StdPicture 介面](stdole.stdpicture.md)

## <a name="see-also"></a>另請參閱

* [.NET Framework 和頻外版本](../get-started/the-net-framework-and-out-of-band-releases.md)
