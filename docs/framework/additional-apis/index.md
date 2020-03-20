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
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="1a2aa-102">其他類別庫和 API</span><span class="sxs-lookup"><span data-stu-id="1a2aa-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="1a2aa-103">.NET 框架在不斷發展。</span><span class="sxs-lookup"><span data-stu-id="1a2aa-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="1a2aa-104">為了改進跨平臺開發並儘早引入新功能，新功能將發佈在頻段 （OOB） 外。</span><span class="sxs-lookup"><span data-stu-id="1a2aa-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="1a2aa-105">本主題列出有提供文件的 OOB 專案。</span><span class="sxs-lookup"><span data-stu-id="1a2aa-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="1a2aa-106">除此之外，某些程式庫會以 .NET Framework 的特定平台或實作為目標。</span><span class="sxs-lookup"><span data-stu-id="1a2aa-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="1a2aa-107">例如，<xref:System.Text.CodePagesEncodingProvider>類使字碼頁編碼可用於使用 .NET 框架開發的 UWP 應用。</span><span class="sxs-lookup"><span data-stu-id="1a2aa-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="1a2aa-108">本主題也會列出這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="1a2aa-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="1a2aa-109">OOB 專案</span><span class="sxs-lookup"><span data-stu-id="1a2aa-109">OOB projects</span></span>
  
| <span data-ttu-id="1a2aa-110">隨附此逐步解說的專案</span><span class="sxs-lookup"><span data-stu-id="1a2aa-110">Project</span></span> | <span data-ttu-id="1a2aa-111">描述</span><span class="sxs-lookup"><span data-stu-id="1a2aa-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="1a2aa-112">提供具備執行緒安全且保證不會再變更其內容的集合。</span><span class="sxs-lookup"><span data-stu-id="1a2aa-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="1a2aa-113">提供以 Windows 的 WinHTTP 介面為基礎之 <xref:System.Net.Http.HttpClient> 的訊息處理常式。</span><span class="sxs-lookup"><span data-stu-id="1a2aa-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="1a2aa-114">提供可利用 SIMD 硬體加速的向量類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="1a2aa-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>|
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="1a2aa-115">TPL 資料流程程式庫提供資料流程元件，來協助增加啟用並行的應用程式之穩定性。</span><span class="sxs-lookup"><span data-stu-id="1a2aa-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="1a2aa-116">平台特定程式庫</span><span class="sxs-lookup"><span data-stu-id="1a2aa-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="1a2aa-117">隨附此逐步解說的專案</span><span class="sxs-lookup"><span data-stu-id="1a2aa-117">Project</span></span> | <span data-ttu-id="1a2aa-118">描述</span><span class="sxs-lookup"><span data-stu-id="1a2aa-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="1a2aa-119">擴展類<xref:System.Text.EncodingProvider>，使字碼頁編碼可用於面向通用 Windows 平臺的應用。</span><span class="sxs-lookup"><span data-stu-id="1a2aa-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="1a2aa-120">私人 API</span><span class="sxs-lookup"><span data-stu-id="1a2aa-120">Private APIs</span></span>  

<span data-ttu-id="1a2aa-121">這些 API 支援產品基礎結構，而且不適合/不支援直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="1a2aa-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="1a2aa-122">微軟.SqlServer.Server.Smiorder屬性.專案屬性</span><span class="sxs-lookup"><span data-stu-id="1a2aa-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="1a2aa-123">系統.例外.準備重新移動方法</span><span class="sxs-lookup"><span data-stu-id="1a2aa-123">System.Exception.PrepForRemoting Method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="1a2aa-124">系統.資料.SqlTypes.SqlChars.流屬性</span><span class="sxs-lookup"><span data-stu-id="1a2aa-124">System.Data.SqlTypes.SqlChars.Stream Property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="1a2aa-125">系統.資料.SqlTypes.SqlStreamChars建構函式</span><span class="sxs-lookup"><span data-stu-id="1a2aa-125">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="1a2aa-126">系統.資料.SqlTypes.SqlStreamChars.CanSeek 屬性</span><span class="sxs-lookup"><span data-stu-id="1a2aa-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="1a2aa-127">系統.資料.SqlTypes.SqlStreamChars.IsNull 屬性</span><span class="sxs-lookup"><span data-stu-id="1a2aa-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="1a2aa-128">系統.資料.SqlTypes.SqlStreamChars.長度屬性</span><span class="sxs-lookup"><span data-stu-id="1a2aa-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="1a2aa-129">系統.資料.SqlTypes.SqlStreamChars.關閉方法</span><span class="sxs-lookup"><span data-stu-id="1a2aa-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="1a2aa-130">系統.資料.SqlTypes.SqlStreamChars.Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="1a2aa-130">System.Data.SqlTypes.SqlStreamChars.Dispose Method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="1a2aa-131">系統.資料.SqlTypes.SqlStreamChars.Flush 方法</span><span class="sxs-lookup"><span data-stu-id="1a2aa-131">System.Data.SqlTypes.SqlStreamChars.Flush Method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="1a2aa-132">系統.資料.SqlTypes.SqlStreamChars.讀取方法</span><span class="sxs-lookup"><span data-stu-id="1a2aa-132">System.Data.SqlTypes.SqlStreamChars.Read Method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="1a2aa-133">系統.資料.SqlTypes.SqlStreamChars.查找方法</span><span class="sxs-lookup"><span data-stu-id="1a2aa-133">System.Data.SqlTypes.SqlStreamChars.Seek Method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="1a2aa-134">系統.資料.SqlTypes.SqlStreamChars.set 長度方法</span><span class="sxs-lookup"><span data-stu-id="1a2aa-134">System.Data.SqlTypes.SqlStreamChars.SetLength Method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="1a2aa-135">系統.資料.SqlTypes.SqlStreamChars.寫入方法</span><span class="sxs-lookup"><span data-stu-id="1a2aa-135">System.Data.SqlTypes.SqlStreamChars.Write Method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="1a2aa-136">系統.IO.記憶體流.內部獲取源和長度方法</span><span class="sxs-lookup"><span data-stu-id="1a2aa-136">System.IO.MemoryStream.InternalGetOriginAndLength Method</span></span>](system.io.memorystream.internalgetoriginandlength.md)
* [<span data-ttu-id="1a2aa-137">系統.Net.連接類</span><span class="sxs-lookup"><span data-stu-id="1a2aa-137">System.Net.Connection Class</span></span>](connection.md)
* [<span data-ttu-id="1a2aa-138">系統.Net.連接.m\_寫入清單欄位</span><span class="sxs-lookup"><span data-stu-id="1a2aa-138">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md)
* [<span data-ttu-id="1a2aa-139">系統.Net.連接組類</span><span class="sxs-lookup"><span data-stu-id="1a2aa-139">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md)
* [<span data-ttu-id="1a2aa-140">系統.Net.連接組.m\_連接清單欄位</span><span class="sxs-lookup"><span data-stu-id="1a2aa-140">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="1a2aa-141">系統.Net.連接流.連接屬性</span><span class="sxs-lookup"><span data-stu-id="1a2aa-141">System.Net.ConnectStream.Connection Property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="1a2aa-142">系統.Net.核心回應資料類</span><span class="sxs-lookup"><span data-stu-id="1a2aa-142">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="1a2aa-143">系統.Net.核心回應資料.m\_回應標題欄位</span><span class="sxs-lookup"><span data-stu-id="1a2aa-143">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="1a2aa-144">系統.Net.核心回應資料.m\_狀態碼欄位</span><span class="sxs-lookup"><span data-stu-id="1a2aa-144">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="1a2aa-145">系統.Net.HttpWeb請求。\_自動重定向欄位</span><span class="sxs-lookup"><span data-stu-id="1a2aa-145">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md)
* [<span data-ttu-id="1a2aa-146">系統.Net.HttpWeb請求。\_核心回應欄位</span><span class="sxs-lookup"><span data-stu-id="1a2aa-146">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="1a2aa-147">系統.Net.HttpWeb請求。\_Http 回應欄位</span><span class="sxs-lookup"><span data-stu-id="1a2aa-147">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md)
* [<span data-ttu-id="1a2aa-148">系統.Net.池流.網路流屬性</span><span class="sxs-lookup"><span data-stu-id="1a2aa-148">System.Net.PooledStream.NetworkStream Property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="1a2aa-149">系統.Net.RtcState 類</span><span class="sxs-lookup"><span data-stu-id="1a2aa-149">System.Net.RtcState class</span></span>](system.net.rtcstate.md)
* [<span data-ttu-id="1a2aa-150">系統.Net.服務點.m\_連接組清單欄位</span><span class="sxs-lookup"><span data-stu-id="1a2aa-150">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="1a2aa-151">系統.Net.服務點管理器.的服務\_點表字段</span><span class="sxs-lookup"><span data-stu-id="1a2aa-151">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="1a2aa-152">系統.Net.TlsStream.m_Worker欄位</span><span class="sxs-lookup"><span data-stu-id="1a2aa-152">System.Net.TlsStream.m_Worker Field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="1a2aa-153">系統.Net.Security.SslState.Ssl協定屬性</span><span class="sxs-lookup"><span data-stu-id="1a2aa-153">System.Net.Security.SslState.SslProtocol Property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="1a2aa-154">系統.服務模式.通道.消息.正文string方法</span><span class="sxs-lookup"><span data-stu-id="1a2aa-154">System.ServiceModel.Channels.Message.BodyToString Method</span></span>](system.servicemodel.channels.message.bodytostring.md)
* [<span data-ttu-id="1a2aa-155">系統.服務模式.通道.消息.編寫開始標題方法</span><span class="sxs-lookup"><span data-stu-id="1a2aa-155">System.ServiceModel.Channels.Message.WriteStartHeaders Method</span></span>](system.servicemodel.channels.message.writestartheaders.md)
* [<span data-ttu-id="1a2aa-156">系統.Windows.診斷.視覺診斷是\_調試器檢查禁用的"測試目的"欄位</span><span class="sxs-lookup"><span data-stu-id="1a2aa-156">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="1a2aa-157">系統.Windows.表單.設計.資料成員欄位編輯器類</span><span class="sxs-lookup"><span data-stu-id="1a2aa-157">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="1a2aa-158">系統.Windows.表單.設計.資料成員清單編輯器類</span><span class="sxs-lookup"><span data-stu-id="1a2aa-158">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="1a2aa-159">系統.Xml.XmlReader.createSqlReader方法</span><span class="sxs-lookup"><span data-stu-id="1a2aa-159">System.Xml.XmlReader.CreateSqlReader Method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="1a2aa-160">阿多德布連接介面</span><span class="sxs-lookup"><span data-stu-id="1a2aa-160">adodb.Connection Interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="1a2aa-161">阿多德布事件原因枚舉</span><span class="sxs-lookup"><span data-stu-id="1a2aa-161">adodb.EventReason Enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="1a2aa-162">阿多德布事件狀態枚舉</span><span class="sxs-lookup"><span data-stu-id="1a2aa-162">adodb.EventStatus Enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="1a2aa-163">stdole。DISPPARAMS 結構</span><span class="sxs-lookup"><span data-stu-id="1a2aa-163">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="1a2aa-164">stdole。EXCEPINFO 結構</span><span class="sxs-lookup"><span data-stu-id="1a2aa-164">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="1a2aa-165">stdole。IFont.Name酒店</span><span class="sxs-lookup"><span data-stu-id="1a2aa-165">stdole.IFont.Name Property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="1a2aa-166">stdole。IFontDisp 介面</span><span class="sxs-lookup"><span data-stu-id="1a2aa-166">stdole.IFontDisp Interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="1a2aa-167">stdole。IPicture.Handle 屬性</span><span class="sxs-lookup"><span data-stu-id="1a2aa-167">stdole.IPicture.Handle Property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="1a2aa-168">stdole。IPictureDisp.Handle 屬性</span><span class="sxs-lookup"><span data-stu-id="1a2aa-168">stdole.IPictureDisp.Handle Property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="1a2aa-169">stdole。斯特芬介面</span><span class="sxs-lookup"><span data-stu-id="1a2aa-169">stdole.StdFont Interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="1a2aa-170">stdole。StdPicture 介面</span><span class="sxs-lookup"><span data-stu-id="1a2aa-170">stdole.StdPicture Interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="1a2aa-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a2aa-171">See also</span></span>

* [<span data-ttu-id="1a2aa-172">.NET Framework 和不定期發行</span><span class="sxs-lookup"><span data-stu-id="1a2aa-172">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
