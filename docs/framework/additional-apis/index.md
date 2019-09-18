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
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="9e343-102">其他類別庫和 API</span><span class="sxs-lookup"><span data-stu-id="9e343-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="9e343-103">.NET Framework 不斷進化。</span><span class="sxs-lookup"><span data-stu-id="9e343-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="9e343-104">為了改善跨平臺開發並及早引進新功能，新功能會以頻外（OOB）發行。</span><span class="sxs-lookup"><span data-stu-id="9e343-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="9e343-105">本主題列出有提供文件的 OOB 專案。</span><span class="sxs-lookup"><span data-stu-id="9e343-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="9e343-106">除此之外，某些程式庫會以 .NET Framework 的特定平台或實作為目標。</span><span class="sxs-lookup"><span data-stu-id="9e343-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="9e343-107">例如， <xref:System.Text.CodePagesEncodingProvider>類別會讓使用 .NET Framework 開發的 UWP 應用程式可以使用字碼頁編碼。</span><span class="sxs-lookup"><span data-stu-id="9e343-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="9e343-108">本主題也會列出這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="9e343-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="9e343-109">OOB 專案</span><span class="sxs-lookup"><span data-stu-id="9e343-109">OOB projects</span></span>
  
| <span data-ttu-id="9e343-110">專案</span><span class="sxs-lookup"><span data-stu-id="9e343-110">Project</span></span> | <span data-ttu-id="9e343-111">描述</span><span class="sxs-lookup"><span data-stu-id="9e343-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="9e343-112">提供具備執行緒安全且保證不會再變更其內容的集合。</span><span class="sxs-lookup"><span data-stu-id="9e343-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="9e343-113">提供以 Windows 的 WinHTTP 介面為基礎之 <xref:System.Net.Http.HttpClient> 的訊息處理常式。</span><span class="sxs-lookup"><span data-stu-id="9e343-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="9e343-114">提供可利用 SIMD 硬體加速的向量類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="9e343-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="9e343-115">TPL 資料流程程式庫提供資料流程元件，來協助增加啟用並行的應用程式之穩定性。</span><span class="sxs-lookup"><span data-stu-id="9e343-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="9e343-116">平台特定程式庫</span><span class="sxs-lookup"><span data-stu-id="9e343-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="9e343-117">專案</span><span class="sxs-lookup"><span data-stu-id="9e343-117">Project</span></span> | <span data-ttu-id="9e343-118">描述</span><span class="sxs-lookup"><span data-stu-id="9e343-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="9e343-119"><xref:System.Text.EncodingProvider>擴充類別，讓以通用 Windows 平臺為目標的應用程式可以使用字碼頁編碼。</span><span class="sxs-lookup"><span data-stu-id="9e343-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="9e343-120">私人 API</span><span class="sxs-lookup"><span data-stu-id="9e343-120">Private APIs</span></span>  

<span data-ttu-id="9e343-121">這些 API 支援產品基礎結構，而且不適合/不支援直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="9e343-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="9e343-122">API 名稱</span><span class="sxs-lookup"><span data-stu-id="9e343-122">API Name</span></span> |
| -------- |
| [<span data-ttu-id="9e343-123">系統 .Net. Connection 類別</span><span class="sxs-lookup"><span data-stu-id="9e343-123">System.Net.Connection Class</span></span>](connection.md) |
| <span data-ttu-id="9e343-124">[[System .net. Connection.\_m WriteList] 欄位](m_writelist.md)</span><span class="sxs-lookup"><span data-stu-id="9e343-124">[System.Net.Connection.m\_WriteList Field](m_writelist.md)</span></span> |
| [<span data-ttu-id="9e343-125">ConnectionGroup 類別</span><span class="sxs-lookup"><span data-stu-id="9e343-125">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md) |
| <span data-ttu-id="9e343-126">[[System .net. ConnectionGroup.\_m ConnectionList] 欄位](m_connectionlist.md)</span><span class="sxs-lookup"><span data-stu-id="9e343-126">[System.Net.ConnectionGroup.m\_ConnectionList Field](m_connectionlist.md)</span></span> |
| [<span data-ttu-id="9e343-127">CoreResponseData 類別</span><span class="sxs-lookup"><span data-stu-id="9e343-127">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md) |
| <span data-ttu-id="9e343-128">[[System .net. CoreResponseData.\_m ResponseHeaders] 欄位](coreresponsedata_m_responseheaders.md)</span><span class="sxs-lookup"><span data-stu-id="9e343-128">[System.Net.CoreResponseData.m\_ResponseHeaders Field](coreresponsedata_m_responseheaders.md)</span></span> |
| <span data-ttu-id="9e343-129">[[System .net. CoreResponseData\_] StatusCode 欄位](coreresponsedata_m_statuscode.md)</span><span class="sxs-lookup"><span data-stu-id="9e343-129">[System.Net.CoreResponseData.m\_StatusCode Field](coreresponsedata_m_statuscode.md)</span></span> |
| [<span data-ttu-id="9e343-130">系統 .Net. HttpWebRequest。\_AutoRedirects 欄位</span><span class="sxs-lookup"><span data-stu-id="9e343-130">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md) |
| [<span data-ttu-id="9e343-131">系統 .Net. HttpWebRequest。\_CoreResponse 欄位</span><span class="sxs-lookup"><span data-stu-id="9e343-131">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md) |
| [<span data-ttu-id="9e343-132">系統 .Net. HttpWebRequest。\_HttpResponse 欄位</span><span class="sxs-lookup"><span data-stu-id="9e343-132">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md) |
| <span data-ttu-id="9e343-133">[[System .net. ServicePoint.\_m ConnectionGroupList] 欄位](m_connectiongrouplist.md)</span><span class="sxs-lookup"><span data-stu-id="9e343-133">[System.Net.ServicePoint.m\_ConnectionGroupList Field](m_connectiongrouplist.md)</span></span> |
| <span data-ttu-id="9e343-134">[[System .net. ServicePointManager.\_s ServicePointTable] 欄位](s_servicepointtable.md)</span><span class="sxs-lookup"><span data-stu-id="9e343-134">[System.Net.ServicePointManager.s\_ServicePointTable Field](s_servicepointtable.md)</span></span> |
| [<span data-ttu-id="9e343-135">VisualDiagnostics. s\_isDebuggerCheckDisabledForTestPurposes 欄位</span><span class="sxs-lookup"><span data-stu-id="9e343-135">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="9e343-136">System.web. DataMemberFieldEditor 類別</span><span class="sxs-lookup"><span data-stu-id="9e343-136">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md) |
| [<span data-ttu-id="9e343-137">System.web. DataMemberListEditor 類別</span><span class="sxs-lookup"><span data-stu-id="9e343-137">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="9e343-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e343-138">See also</span></span>

- [<span data-ttu-id="9e343-139">.NET Framework 和不定期發行</span><span class="sxs-lookup"><span data-stu-id="9e343-139">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
