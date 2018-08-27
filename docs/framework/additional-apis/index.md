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
ms.openlocfilehash: 049268c29946e95ca7bb194f6cae38baf8f060f6
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933526"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="809e6-102">其他類別庫和 API</span><span class="sxs-lookup"><span data-stu-id="809e6-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="809e6-103">.NET Framework 一直不斷進化。</span><span class="sxs-lookup"><span data-stu-id="809e6-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="809e6-104">若要改善跨平台開發，並及早引入新功能，會發行 out-of-band (OOB) 的新功能。</span><span class="sxs-lookup"><span data-stu-id="809e6-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="809e6-105">本主題列出有提供文件的 OOB 專案。</span><span class="sxs-lookup"><span data-stu-id="809e6-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="809e6-106">除此之外，某些程式庫會以 .NET Framework 的特定平台或實作為目標。</span><span class="sxs-lookup"><span data-stu-id="809e6-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="809e6-107">比方說，<xref:System.Text.CodePagesEncodingProvider>類別會使用.NET Framework 開發的 UWP 應用程式提供字碼頁編碼方式。</span><span class="sxs-lookup"><span data-stu-id="809e6-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="809e6-108">本主題也會列出這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="809e6-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="809e6-109">OOB 專案</span><span class="sxs-lookup"><span data-stu-id="809e6-109">OOB projects</span></span>
  
| <span data-ttu-id="809e6-110">專案</span><span class="sxs-lookup"><span data-stu-id="809e6-110">Project</span></span> | <span data-ttu-id="809e6-111">描述</span><span class="sxs-lookup"><span data-stu-id="809e6-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="809e6-112">提供具備執行緒安全且保證不會再變更其內容的集合。</span><span class="sxs-lookup"><span data-stu-id="809e6-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="809e6-113">提供以 Windows 的 WinHTTP 介面為基礎之 <xref:System.Net.Http.HttpClient> 的訊息處理常式。</span><span class="sxs-lookup"><span data-stu-id="809e6-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="809e6-114">System.Numerics.Vectors (英文)</span><span class="sxs-lookup"><span data-stu-id="809e6-114">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="809e6-115">提供可利用 SIMD 硬體加速的向量類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="809e6-115">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="809e6-116">TPL 資料流程程式庫提供資料流程元件，來協助增加啟用並行的應用程式之穩定性。</span><span class="sxs-lookup"><span data-stu-id="809e6-116">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="809e6-117">平台特定程式庫</span><span class="sxs-lookup"><span data-stu-id="809e6-117">Platform-specific libraries</span></span>
  
| <span data-ttu-id="809e6-118">專案</span><span class="sxs-lookup"><span data-stu-id="809e6-118">Project</span></span> | <span data-ttu-id="809e6-119">描述</span><span class="sxs-lookup"><span data-stu-id="809e6-119">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="809e6-120">擴充<xref:System.Text.EncodingProvider>類別，以使用於通用 Windows 平台為目標的應用程式的字碼頁編碼方式。</span><span class="sxs-lookup"><span data-stu-id="809e6-120">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="809e6-121">私人 API</span><span class="sxs-lookup"><span data-stu-id="809e6-121">Private APIs</span></span>  

<span data-ttu-id="809e6-122">這些 API 支援產品基礎結構，而且不適合/不支援直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="809e6-122">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="809e6-123">API 名稱</span><span class="sxs-lookup"><span data-stu-id="809e6-123">API Name</span></span> |
| -------- |
| [<span data-ttu-id="809e6-124">System.Net.Connection 類別</span><span class="sxs-lookup"><span data-stu-id="809e6-124">System.Net.Connection Class</span></span>](../../../docs/framework/additional-apis/connection.md) |
| [<span data-ttu-id="809e6-125">System.Net.Connection.m\_WriteList 欄位</span><span class="sxs-lookup"><span data-stu-id="809e6-125">System.Net.Connection.m\_WriteList Field</span></span>](../../../docs/framework/additional-apis/m_writelist.md) |
| [<span data-ttu-id="809e6-126">System.Net.ConnectionGroup 類別</span><span class="sxs-lookup"><span data-stu-id="809e6-126">System.Net.ConnectionGroup Class</span></span>](../../../docs/framework/additional-apis/connectiongroup.md) |
| [<span data-ttu-id="809e6-127">System.Net.ConnectionGroup.m\_ConnectionList 欄位</span><span class="sxs-lookup"><span data-stu-id="809e6-127">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [<span data-ttu-id="809e6-128">System.Net.CoreResponseData 類別</span><span class="sxs-lookup"><span data-stu-id="809e6-128">System.Net.CoreResponseData Class</span></span>](../../../docs/framework/additional-apis/coreresponsedata.md) |
| [<span data-ttu-id="809e6-129">System.Net.CoreResponseData.m\_ResponseHeaders 欄位</span><span class="sxs-lookup"><span data-stu-id="809e6-129">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](../../../docs/framework/additional-apis/coreresponsedata_m_responseheaders.md) |
| [<span data-ttu-id="809e6-130">System.Net.CoreResponseData.m\_StatusCode 欄位</span><span class="sxs-lookup"><span data-stu-id="809e6-130">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](../../../docs/framework/additional-apis/coreresponsedata_m_statuscode.md) |
| [<span data-ttu-id="809e6-131">System.Net.HttpWebRequest。\_AutoRedirects 欄位</span><span class="sxs-lookup"><span data-stu-id="809e6-131">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](../../../docs/framework/additional-apis/_autoredirects.md) |
| [<span data-ttu-id="809e6-132">System.Net.HttpWebRequest。\_CoreResponse 欄位</span><span class="sxs-lookup"><span data-stu-id="809e6-132">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](../../../docs/framework/additional-apis/httpwebrequest__coreresponse.md) |
| [<span data-ttu-id="809e6-133">System.Net.HttpWebRequest。\_HttpResponse 欄位</span><span class="sxs-lookup"><span data-stu-id="809e6-133">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](../../../docs/framework/additional-apis/_httpresponse.md) |
| [<span data-ttu-id="809e6-134">System.Net.ServicePoint.m\_ConnectionGroupList 欄位</span><span class="sxs-lookup"><span data-stu-id="809e6-134">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [<span data-ttu-id="809e6-135">System.Net.ServicePointManager.s\_ServicePointTable 欄位</span><span class="sxs-lookup"><span data-stu-id="809e6-135">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [<span data-ttu-id="809e6-136">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes 欄位</span><span class="sxs-lookup"><span data-stu-id="809e6-136">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="809e6-137">System.Windows.Forms.Design.DataMemberFieldEditor 類別</span><span class="sxs-lookup"><span data-stu-id="809e6-137">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [<span data-ttu-id="809e6-138">System.Windows.Forms.Design.DataMemberListEditor 類別</span><span class="sxs-lookup"><span data-stu-id="809e6-138">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="809e6-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="809e6-139">See also</span></span>

[<span data-ttu-id="809e6-140">.NET Framework 和不定期發行</span><span class="sxs-lookup"><span data-stu-id="809e6-140">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
