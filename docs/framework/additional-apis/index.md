---
title: "其他類別庫和 API | Microsoft Docs"
ms.custom: 
ms.date: 04/12/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: 12
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: b53b8acc2a6c56db6a9d8a9b7c685a2d400a53e1
ms.openlocfilehash: 34815268b707aa70d174a1bbc04c32276db8412d
ms.contentlocale: zh-tw
ms.lasthandoff: 05/02/2017

---

# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="af081-102">其他類別庫和 API</span><span class="sxs-lookup"><span data-stu-id="af081-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="af081-103">由於 .NET Framework 會持續演變，因此為了改善跨平台開發工作或讓客戶早點採用新功能，我們會不定期 (Out of Band，OOB) 發行新功能。</span><span class="sxs-lookup"><span data-stu-id="af081-103">The .NET Framework is constantly evolving and in order to improve cross-platform development or to introduce new functionality early to our customers, we release new features out of band (OOB).</span></span> <span data-ttu-id="af081-104">本主題列出有提供文件的 OOB 專案。</span><span class="sxs-lookup"><span data-stu-id="af081-104">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="af081-105">除此之外，某些程式庫會以 .NET Framework 的特定平台或實作為目標。</span><span class="sxs-lookup"><span data-stu-id="af081-105">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="af081-106">例如，<xref:System.Text.CodePagesEncodingProvider> 類別會向使用 .NET Framework 開發的 UWP 應用程式提供字碼頁編碼。</span><span class="sxs-lookup"><span data-stu-id="af081-106">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="af081-107">本主題也會列出這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="af081-107">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="af081-108">OOB 專案</span><span class="sxs-lookup"><span data-stu-id="af081-108">OOB projects</span></span>
  
| <span data-ttu-id="af081-109">專案</span><span class="sxs-lookup"><span data-stu-id="af081-109">Project</span></span> | <span data-ttu-id="af081-110">描述</span><span class="sxs-lookup"><span data-stu-id="af081-110">Description</span></span> |  
| ------- | ----------- |  
| <span data-ttu-id="af081-111"><xref:System.Collections.Immutable></span><span class="sxs-lookup"><span data-stu-id="af081-111"><xref:System.Collections.Immutable></span></span> | <span data-ttu-id="af081-112">提供具備執行緒安全且保證不會再變更其內容的集合。</span><span class="sxs-lookup"><span data-stu-id="af081-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <span data-ttu-id="af081-113"><xref:System.Net.Http.WinHttpHandler></span><span class="sxs-lookup"><span data-stu-id="af081-113"><xref:System.Net.Http.WinHttpHandler></span></span> | <span data-ttu-id="af081-114">為 <xref:System.Net.Http.HttpClient> 提供以 Windows 的 WinHTTP 介面為基礎的訊息處理常式。</span><span class="sxs-lookup"><span data-stu-id="af081-114">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="af081-115">System.Numerics.Vectors (英文)</span><span class="sxs-lookup"><span data-stu-id="af081-115">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="af081-116">提供可利用 SIMD 硬體加速的向量類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="af081-116">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <span data-ttu-id="af081-117"><xref:System.Threading.Tasks.Dataflow></span><span class="sxs-lookup"><span data-stu-id="af081-117"><xref:System.Threading.Tasks.Dataflow></span></span> | <span data-ttu-id="af081-118">TPL 資料流程程式庫提供資料流程元件，來協助增加啟用並行的應用程式之穩定性。</span><span class="sxs-lookup"><span data-stu-id="af081-118">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="af081-119">平台特定程式庫</span><span class="sxs-lookup"><span data-stu-id="af081-119">Platform-specific libraries</span></span>
  
| <span data-ttu-id="af081-120">專案</span><span class="sxs-lookup"><span data-stu-id="af081-120">Project</span></span> | <span data-ttu-id="af081-121">描述</span><span class="sxs-lookup"><span data-stu-id="af081-121">Description</span></span> |  
| ------- | ----------- |  
| <span data-ttu-id="af081-122"><xref:System.Text.CodePagesEncodingProvider></span><span class="sxs-lookup"><span data-stu-id="af081-122"><xref:System.Text.CodePagesEncodingProvider></span></span> | <span data-ttu-id="af081-123">擴充 <xref:System.Text.EncodingProvider> 類別，來向以通用 Windows 平台為目標的應用程式提供字碼頁編碼。</span><span class="sxs-lookup"><span data-stu-id="af081-123">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="af081-124">私人 API</span><span class="sxs-lookup"><span data-stu-id="af081-124">Private APIs</span></span>  

<span data-ttu-id="af081-125">這些 API 支援產品基礎結構，而且不適合/不支援直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="af081-125">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="af081-126">API 名稱</span><span class="sxs-lookup"><span data-stu-id="af081-126">API Name</span></span> |  
| -------- |  
| [<span data-ttu-id="af081-127">s_isDebuggerCheckDisabledForTestPurposes 欄位</span><span class="sxs-lookup"><span data-stu-id="af081-127">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |  
| [<span data-ttu-id="af081-128">DataMemberFieldEditor 類別</span><span class="sxs-lookup"><span data-stu-id="af081-128">DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |  
| [<span data-ttu-id="af081-129">DataMemberListEditor 類別</span><span class="sxs-lookup"><span data-stu-id="af081-129">DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |  
  
## <a name="see-also"></a><span data-ttu-id="af081-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="af081-130">See also</span></span>

[<span data-ttu-id="af081-131">.NET Framework 和不定期發行</span><span class="sxs-lookup"><span data-stu-id="af081-131">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)

