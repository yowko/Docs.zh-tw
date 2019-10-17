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
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="3cc78-102">其他類別庫和 API</span><span class="sxs-lookup"><span data-stu-id="3cc78-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="3cc78-103">.NET Framework 不斷進化。</span><span class="sxs-lookup"><span data-stu-id="3cc78-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="3cc78-104">為了改善跨平臺開發並及早引進新功能，新功能會以頻外（OOB）發行。</span><span class="sxs-lookup"><span data-stu-id="3cc78-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="3cc78-105">本主題列出有提供文件的 OOB 專案。</span><span class="sxs-lookup"><span data-stu-id="3cc78-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="3cc78-106">除此之外，某些程式庫會以 .NET Framework 的特定平台或實作為目標。</span><span class="sxs-lookup"><span data-stu-id="3cc78-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="3cc78-107">例如，@no__t 0 類別可以讓使用 .NET Framework 開發的 UWP 應用程式使用字碼頁編碼。</span><span class="sxs-lookup"><span data-stu-id="3cc78-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="3cc78-108">本主題也會列出這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="3cc78-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="3cc78-109">OOB 專案</span><span class="sxs-lookup"><span data-stu-id="3cc78-109">OOB projects</span></span>
  
| <span data-ttu-id="3cc78-110">專案</span><span class="sxs-lookup"><span data-stu-id="3cc78-110">Project</span></span> | <span data-ttu-id="3cc78-111">描述</span><span class="sxs-lookup"><span data-stu-id="3cc78-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="3cc78-112">提供具備執行緒安全且保證不會再變更其內容的集合。</span><span class="sxs-lookup"><span data-stu-id="3cc78-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="3cc78-113">提供以 Windows 的 WinHTTP 介面為基礎之 <xref:System.Net.Http.HttpClient> 的訊息處理常式。</span><span class="sxs-lookup"><span data-stu-id="3cc78-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="3cc78-114">提供可利用 SIMD 硬體加速的向量類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="3cc78-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="3cc78-115">TPL 資料流程程式庫提供資料流程元件，來協助增加啟用並行的應用程式之穩定性。</span><span class="sxs-lookup"><span data-stu-id="3cc78-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="3cc78-116">平台特定程式庫</span><span class="sxs-lookup"><span data-stu-id="3cc78-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="3cc78-117">專案</span><span class="sxs-lookup"><span data-stu-id="3cc78-117">Project</span></span> | <span data-ttu-id="3cc78-118">描述</span><span class="sxs-lookup"><span data-stu-id="3cc78-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="3cc78-119">擴充 @no__t 0 類別，讓以通用 Windows 平臺為目標的應用程式可以使用字碼頁編碼。</span><span class="sxs-lookup"><span data-stu-id="3cc78-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="3cc78-120">私人 API</span><span class="sxs-lookup"><span data-stu-id="3cc78-120">Private APIs</span></span>  

<span data-ttu-id="3cc78-121">這些 API 支援產品基礎結構，而且不適合/不支援直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="3cc78-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="3cc78-122">SmiOrderProperty. Item 屬性</span><span class="sxs-lookup"><span data-stu-id="3cc78-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="3cc78-123">PrepForRemoting 方法</span><span class="sxs-lookup"><span data-stu-id="3cc78-123">System.Exception.PrepForRemoting Method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="3cc78-124">SqlTypes. SqlChars 資料流程屬性</span><span class="sxs-lookup"><span data-stu-id="3cc78-124">System.Data.SqlTypes.SqlChars.Stream Property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="3cc78-125">SqlTypes. SqlStreamChars 函數</span><span class="sxs-lookup"><span data-stu-id="3cc78-125">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="3cc78-126">SqlTypes. SqlStreamChars. CanSeek 屬性</span><span class="sxs-lookup"><span data-stu-id="3cc78-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="3cc78-127">SqlTypes. SqlStreamChars. IsNull 屬性</span><span class="sxs-lookup"><span data-stu-id="3cc78-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="3cc78-128">SqlTypes. SqlStreamChars. Length 屬性</span><span class="sxs-lookup"><span data-stu-id="3cc78-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="3cc78-129">SqlTypes. SqlStreamChars. Close 方法</span><span class="sxs-lookup"><span data-stu-id="3cc78-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="3cc78-130">SqlTypes. SqlStreamChars. Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="3cc78-130">System.Data.SqlTypes.SqlStreamChars.Dispose Method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="3cc78-131">SqlTypes. SqlStreamChars. Flush 方法</span><span class="sxs-lookup"><span data-stu-id="3cc78-131">System.Data.SqlTypes.SqlStreamChars.Flush Method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="3cc78-132">SqlTypes. SqlStreamChars. Read 方法</span><span class="sxs-lookup"><span data-stu-id="3cc78-132">System.Data.SqlTypes.SqlStreamChars.Read Method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="3cc78-133">SqlTypes. SqlStreamChars. Seek 方法</span><span class="sxs-lookup"><span data-stu-id="3cc78-133">System.Data.SqlTypes.SqlStreamChars.Seek Method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="3cc78-134">SqlTypes. SqlStreamChars. SetLength 方法</span><span class="sxs-lookup"><span data-stu-id="3cc78-134">System.Data.SqlTypes.SqlStreamChars.SetLength Method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="3cc78-135">SqlTypes. SqlStreamChars. Write 方法</span><span class="sxs-lookup"><span data-stu-id="3cc78-135">System.Data.SqlTypes.SqlStreamChars.Write Method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="3cc78-136">系統 .Net. Connection 類別</span><span class="sxs-lookup"><span data-stu-id="3cc78-136">System.Net.Connection Class</span></span>](connection.md)
* <span data-ttu-id="3cc78-137">[[系統 .Net]。 m @ no__t-1WriteList 欄位](m_writelist.md)</span><span class="sxs-lookup"><span data-stu-id="3cc78-137">[System.Net.Connection.m\_WriteList Field](m_writelist.md)</span></span>
* [<span data-ttu-id="3cc78-138">ConnectionGroup 類別</span><span class="sxs-lookup"><span data-stu-id="3cc78-138">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md)
* [<span data-ttu-id="3cc78-139">ConnectionGroup. m @ no__t-1ConnectionList 欄位</span><span class="sxs-lookup"><span data-stu-id="3cc78-139">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="3cc78-140">CoreResponseData 類別</span><span class="sxs-lookup"><span data-stu-id="3cc78-140">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="3cc78-141">CoreResponseData. m @ no__t-1ResponseHeaders 欄位</span><span class="sxs-lookup"><span data-stu-id="3cc78-141">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="3cc78-142">CoreResponseData. m @ no__t-1StatusCode 欄位</span><span class="sxs-lookup"><span data-stu-id="3cc78-142">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="3cc78-143">HttpWebRequest. \_AutoRedirects 欄位</span><span class="sxs-lookup"><span data-stu-id="3cc78-143">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md)
* [<span data-ttu-id="3cc78-144">HttpWebRequest. \_CoreResponse 欄位</span><span class="sxs-lookup"><span data-stu-id="3cc78-144">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="3cc78-145">HttpWebRequest. \_HttpResponse 欄位</span><span class="sxs-lookup"><span data-stu-id="3cc78-145">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md)
* [<span data-ttu-id="3cc78-146">ServicePoint. m @ no__t-1ConnectionGroupList 欄位</span><span class="sxs-lookup"><span data-stu-id="3cc78-146">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="3cc78-147">System .Net. ServicePointManager. s @ no__t-1ServicePointTable 欄位</span><span class="sxs-lookup"><span data-stu-id="3cc78-147">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="3cc78-148">VisualDiagnostics. s @ no__t-1isDebuggerCheckDisabledForTestPurposes 欄位</span><span class="sxs-lookup"><span data-stu-id="3cc78-148">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="3cc78-149">System.web. DataMemberFieldEditor 類別</span><span class="sxs-lookup"><span data-stu-id="3cc78-149">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="3cc78-150">System.web. DataMemberListEditor 類別</span><span class="sxs-lookup"><span data-stu-id="3cc78-150">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="3cc78-151">adodb.連接介面</span><span class="sxs-lookup"><span data-stu-id="3cc78-151">adodb.Connection Interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="3cc78-152">adodb.EventReason 列舉</span><span class="sxs-lookup"><span data-stu-id="3cc78-152">adodb.EventReason Enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="3cc78-153">adodb.EventStatus 列舉</span><span class="sxs-lookup"><span data-stu-id="3cc78-153">adodb.EventStatus Enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="3cc78-154">stdole.DISPPARAMS 結構</span><span class="sxs-lookup"><span data-stu-id="3cc78-154">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="3cc78-155">stdole.EXCEPINFO 結構</span><span class="sxs-lookup"><span data-stu-id="3cc78-155">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="3cc78-156">stdole.IFont.Name 屬性</span><span class="sxs-lookup"><span data-stu-id="3cc78-156">stdole.IFont.Name Property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="3cc78-157">stdole.IFontDisp 介面</span><span class="sxs-lookup"><span data-stu-id="3cc78-157">stdole.IFontDisp Interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="3cc78-158">stdole.圖片屬性</span><span class="sxs-lookup"><span data-stu-id="3cc78-158">stdole.IPicture.Handle Property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="3cc78-159">stdole.IPictureDisp 屬性</span><span class="sxs-lookup"><span data-stu-id="3cc78-159">stdole.IPictureDisp.Handle Property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="3cc78-160">stdole.StdFont 介面</span><span class="sxs-lookup"><span data-stu-id="3cc78-160">stdole.StdFont Interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="3cc78-161">stdole.StdPicture 介面</span><span class="sxs-lookup"><span data-stu-id="3cc78-161">stdole.StdPicture Interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="3cc78-162">請參閱</span><span class="sxs-lookup"><span data-stu-id="3cc78-162">See also</span></span>

* [<span data-ttu-id="3cc78-163">.NET Framework 和不定期發行</span><span class="sxs-lookup"><span data-stu-id="3cc78-163">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
