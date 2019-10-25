---
title: 其他類別庫和 API
ms.date: 10/17/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 4b47847e9d6e9424d4442d655c40a637383c7229
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847074"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="51867-102">其他類別庫和 API</span><span class="sxs-lookup"><span data-stu-id="51867-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="51867-103">.NET Framework 不斷進化。</span><span class="sxs-lookup"><span data-stu-id="51867-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="51867-104">為了改善跨平臺開發並及早引進新功能，新功能會以頻外（OOB）發行。</span><span class="sxs-lookup"><span data-stu-id="51867-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="51867-105">本主題列出有提供文件的 OOB 專案。</span><span class="sxs-lookup"><span data-stu-id="51867-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="51867-106">除此之外，某些程式庫會以 .NET Framework 的特定平台或實作為目標。</span><span class="sxs-lookup"><span data-stu-id="51867-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="51867-107">例如，<xref:System.Text.CodePagesEncodingProvider> 類別可以讓使用 .NET Framework 開發的 UWP 應用程式使用字碼頁編碼。</span><span class="sxs-lookup"><span data-stu-id="51867-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="51867-108">本主題也會列出這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="51867-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="51867-109">OOB 專案</span><span class="sxs-lookup"><span data-stu-id="51867-109">OOB projects</span></span>
  
| <span data-ttu-id="51867-110">專案</span><span class="sxs-lookup"><span data-stu-id="51867-110">Project</span></span> | <span data-ttu-id="51867-111">描述</span><span class="sxs-lookup"><span data-stu-id="51867-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="51867-112">提供具備執行緒安全且保證不會再變更其內容的集合。</span><span class="sxs-lookup"><span data-stu-id="51867-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="51867-113">提供以 Windows 的 WinHTTP 介面為基礎之 <xref:System.Net.Http.HttpClient> 的訊息處理常式。</span><span class="sxs-lookup"><span data-stu-id="51867-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="51867-114">提供可利用 SIMD 硬體加速的向量類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="51867-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="51867-115">TPL 資料流程程式庫提供資料流程元件，來協助增加啟用並行的應用程式之穩定性。</span><span class="sxs-lookup"><span data-stu-id="51867-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="51867-116">平台特定程式庫</span><span class="sxs-lookup"><span data-stu-id="51867-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="51867-117">專案</span><span class="sxs-lookup"><span data-stu-id="51867-117">Project</span></span> | <span data-ttu-id="51867-118">描述</span><span class="sxs-lookup"><span data-stu-id="51867-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="51867-119">擴充 <xref:System.Text.EncodingProvider> 類別，讓以通用 Windows 平臺為目標的應用程式可以使用字碼頁編碼。</span><span class="sxs-lookup"><span data-stu-id="51867-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="51867-120">私人 API</span><span class="sxs-lookup"><span data-stu-id="51867-120">Private APIs</span></span>  

<span data-ttu-id="51867-121">這些 API 支援產品基礎結構，而且不適合/不支援直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="51867-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="51867-122">SmiOrderProperty. Item 屬性</span><span class="sxs-lookup"><span data-stu-id="51867-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="51867-123">PrepForRemoting 方法</span><span class="sxs-lookup"><span data-stu-id="51867-123">System.Exception.PrepForRemoting Method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="51867-124">SqlTypes. SqlChars 資料流程屬性</span><span class="sxs-lookup"><span data-stu-id="51867-124">System.Data.SqlTypes.SqlChars.Stream Property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="51867-125">SqlTypes. SqlStreamChars 函數</span><span class="sxs-lookup"><span data-stu-id="51867-125">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="51867-126">SqlTypes. SqlStreamChars. CanSeek 屬性</span><span class="sxs-lookup"><span data-stu-id="51867-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="51867-127">SqlTypes. SqlStreamChars. IsNull 屬性</span><span class="sxs-lookup"><span data-stu-id="51867-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="51867-128">SqlTypes. SqlStreamChars. Length 屬性</span><span class="sxs-lookup"><span data-stu-id="51867-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="51867-129">SqlTypes. SqlStreamChars. Close 方法</span><span class="sxs-lookup"><span data-stu-id="51867-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="51867-130">SqlTypes. SqlStreamChars. Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="51867-130">System.Data.SqlTypes.SqlStreamChars.Dispose Method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="51867-131">SqlTypes. SqlStreamChars. Flush 方法</span><span class="sxs-lookup"><span data-stu-id="51867-131">System.Data.SqlTypes.SqlStreamChars.Flush Method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="51867-132">SqlTypes. SqlStreamChars. Read 方法</span><span class="sxs-lookup"><span data-stu-id="51867-132">System.Data.SqlTypes.SqlStreamChars.Read Method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="51867-133">SqlTypes. SqlStreamChars. Seek 方法</span><span class="sxs-lookup"><span data-stu-id="51867-133">System.Data.SqlTypes.SqlStreamChars.Seek Method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="51867-134">SqlTypes. SqlStreamChars. SetLength 方法</span><span class="sxs-lookup"><span data-stu-id="51867-134">System.Data.SqlTypes.SqlStreamChars.SetLength Method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="51867-135">SqlTypes. SqlStreamChars. Write 方法</span><span class="sxs-lookup"><span data-stu-id="51867-135">System.Data.SqlTypes.SqlStreamChars.Write Method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="51867-136">系統 .Net. Connection 類別</span><span class="sxs-lookup"><span data-stu-id="51867-136">System.Net.Connection Class</span></span>](connection.md)
* <span data-ttu-id="51867-137">[[系統 .Net]\_WriteList 欄位](m_writelist.md)</span><span class="sxs-lookup"><span data-stu-id="51867-137">[System.Net.Connection.m\_WriteList Field](m_writelist.md)</span></span>
* [<span data-ttu-id="51867-138">ConnectionGroup 類別</span><span class="sxs-lookup"><span data-stu-id="51867-138">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md)
* [<span data-ttu-id="51867-139">System .Net. ConnectionGroup\_ConnectionList 欄位</span><span class="sxs-lookup"><span data-stu-id="51867-139">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="51867-140">ConnectStream 連接屬性</span><span class="sxs-lookup"><span data-stu-id="51867-140">System.Net.ConnectStream.Connection Property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="51867-141">CoreResponseData 類別</span><span class="sxs-lookup"><span data-stu-id="51867-141">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="51867-142">System .Net. CoreResponseData\_ResponseHeaders 欄位</span><span class="sxs-lookup"><span data-stu-id="51867-142">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="51867-143">系統 .Net. CoreResponseData\_StatusCode 欄位</span><span class="sxs-lookup"><span data-stu-id="51867-143">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md)
* <span data-ttu-id="51867-144">[[System .Net. HttpWebRequest.\_AutoRedirects] 欄位](_autoredirects.md)</span><span class="sxs-lookup"><span data-stu-id="51867-144">[System.Net.HttpWebRequest.\_AutoRedirects Field](_autoredirects.md)</span></span>
* <span data-ttu-id="51867-145">[[System .Net. HttpWebRequest.\_CoreResponse] 欄位](httpwebrequest__coreresponse.md)</span><span class="sxs-lookup"><span data-stu-id="51867-145">[System.Net.HttpWebRequest.\_CoreResponse Field](httpwebrequest__coreresponse.md)</span></span>
* <span data-ttu-id="51867-146">[[System .Net. HttpWebRequest.\_HttpResponse] 欄位](_httpresponse.md)</span><span class="sxs-lookup"><span data-stu-id="51867-146">[System.Net.HttpWebRequest.\_HttpResponse Field](_httpresponse.md)</span></span>
* [<span data-ttu-id="51867-147">System .Net. PooledStream. NetworkStream 屬性</span><span class="sxs-lookup"><span data-stu-id="51867-147">System.Net.PooledStream.NetworkStream Property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="51867-148">System .Net. ServicePoint\_ConnectionGroupList 欄位</span><span class="sxs-lookup"><span data-stu-id="51867-148">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md)
* <span data-ttu-id="51867-149">[[System .Net. ServicePointManager\_ServicePointTable] 欄位](s_servicepointtable.md)</span><span class="sxs-lookup"><span data-stu-id="51867-149">[System.Net.ServicePointManager.s\_ServicePointTable Field](s_servicepointtable.md)</span></span>
* <span data-ttu-id="51867-150">[[系統 .Net. TlsStream. m_Worker] 欄位](system.net.tlsstream.m_worker.md)</span><span class="sxs-lookup"><span data-stu-id="51867-150">[System.Net.TlsStream.m_Worker Field](system.net.tlsstream.m_worker.md)</span></span>
* [<span data-ttu-id="51867-151">SslState. SslProtocol 屬性</span><span class="sxs-lookup"><span data-stu-id="51867-151">System.Net.Security.SslState.SslProtocol Property</span></span>](system.net.security.sslstate.sslprotocol.md)
* <span data-ttu-id="51867-152">[VisualDiagnostics [\_isDebuggerCheckDisabledForTestPurposes] 欄位](s-isdebuggercheckdisabledfortestpurposes-field.md)</span><span class="sxs-lookup"><span data-stu-id="51867-152">[System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field](s-isdebuggercheckdisabledfortestpurposes-field.md)</span></span>
* [<span data-ttu-id="51867-153">System.web. DataMemberFieldEditor 類別</span><span class="sxs-lookup"><span data-stu-id="51867-153">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="51867-154">System.web. DataMemberListEditor 類別</span><span class="sxs-lookup"><span data-stu-id="51867-154">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="51867-155">System.web. CreateSqlReader 方法</span><span class="sxs-lookup"><span data-stu-id="51867-155">System.Xml.XmlReader.CreateSqlReader Method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="51867-156">adodb.連接介面</span><span class="sxs-lookup"><span data-stu-id="51867-156">adodb.Connection Interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="51867-157">adodb.EventReason 列舉</span><span class="sxs-lookup"><span data-stu-id="51867-157">adodb.EventReason Enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="51867-158">adodb.EventStatus 列舉</span><span class="sxs-lookup"><span data-stu-id="51867-158">adodb.EventStatus Enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="51867-159">stdole.DISPPARAMS 結構</span><span class="sxs-lookup"><span data-stu-id="51867-159">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="51867-160">stdole.EXCEPINFO 結構</span><span class="sxs-lookup"><span data-stu-id="51867-160">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="51867-161">stdole.IFont.Name 屬性</span><span class="sxs-lookup"><span data-stu-id="51867-161">stdole.IFont.Name Property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="51867-162">stdole.IFontDisp 介面</span><span class="sxs-lookup"><span data-stu-id="51867-162">stdole.IFontDisp Interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="51867-163">stdole.圖片屬性</span><span class="sxs-lookup"><span data-stu-id="51867-163">stdole.IPicture.Handle Property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="51867-164">stdole.IPictureDisp 屬性</span><span class="sxs-lookup"><span data-stu-id="51867-164">stdole.IPictureDisp.Handle Property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="51867-165">stdole.StdFont 介面</span><span class="sxs-lookup"><span data-stu-id="51867-165">stdole.StdFont Interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="51867-166">stdole.StdPicture 介面</span><span class="sxs-lookup"><span data-stu-id="51867-166">stdole.StdPicture Interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="51867-167">請參閱</span><span class="sxs-lookup"><span data-stu-id="51867-167">See also</span></span>

* [<span data-ttu-id="51867-168">.NET Framework 和不定期發行</span><span class="sxs-lookup"><span data-stu-id="51867-168">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
