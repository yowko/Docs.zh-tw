---
title: "其他類別庫和 API"
ms.custom: 
ms.date: 04/12/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e3bb7a7c53cbca8bbd4026b46ce59589cef22382
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="f3332-102">其他類別庫和 API</span><span class="sxs-lookup"><span data-stu-id="f3332-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="f3332-103">由於 .NET Framework 會持續演變，因此為了改善跨平台開發工作或讓客戶早點採用新功能，我們會不定期 (Out of Band，OOB) 發行新功能。</span><span class="sxs-lookup"><span data-stu-id="f3332-103">The .NET Framework is constantly evolving and in order to improve cross-platform development or to introduce new functionality early to our customers, we release new features out of band (OOB).</span></span> <span data-ttu-id="f3332-104">本主題列出有提供文件的 OOB 專案。</span><span class="sxs-lookup"><span data-stu-id="f3332-104">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="f3332-105">除此之外，某些程式庫會以 .NET Framework 的特定平台或實作為目標。</span><span class="sxs-lookup"><span data-stu-id="f3332-105">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="f3332-106">例如，<xref:System.Text.CodePagesEncodingProvider>類別使字碼頁編碼方式可使用.NET Framework 開發 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f3332-106">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="f3332-107">本主題也會列出這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="f3332-107">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="f3332-108">OOB 專案</span><span class="sxs-lookup"><span data-stu-id="f3332-108">OOB projects</span></span>
  
| <span data-ttu-id="f3332-109">Project</span><span class="sxs-lookup"><span data-stu-id="f3332-109">Project</span></span> | <span data-ttu-id="f3332-110">描述</span><span class="sxs-lookup"><span data-stu-id="f3332-110">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="f3332-111">提供具備執行緒安全且保證不會再變更其內容的集合。</span><span class="sxs-lookup"><span data-stu-id="f3332-111">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="f3332-112">提供以 Windows 的 WinHTTP 介面為基礎之 <xref:System.Net.Http.HttpClient> 的訊息處理常式。</span><span class="sxs-lookup"><span data-stu-id="f3332-112">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="f3332-113">System.Numerics.Vectors (英文)</span><span class="sxs-lookup"><span data-stu-id="f3332-113">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="f3332-114">提供可利用 SIMD 硬體加速的向量類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="f3332-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="f3332-115">TPL 資料流程程式庫提供資料流程元件，來協助增加啟用並行的應用程式之穩定性。</span><span class="sxs-lookup"><span data-stu-id="f3332-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="f3332-116">平台特定程式庫</span><span class="sxs-lookup"><span data-stu-id="f3332-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="f3332-117">專案</span><span class="sxs-lookup"><span data-stu-id="f3332-117">Project</span></span> | <span data-ttu-id="f3332-118">說明</span><span class="sxs-lookup"><span data-stu-id="f3332-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="f3332-119">擴充<xref:System.Text.EncodingProvider>供通用 Windows 平台為目標的應用程式程式碼頁編碼方式的類別。</span><span class="sxs-lookup"><span data-stu-id="f3332-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="f3332-120">私人 API</span><span class="sxs-lookup"><span data-stu-id="f3332-120">Private APIs</span></span>  

<span data-ttu-id="f3332-121">這些 API 支援產品基礎結構，而且不適合/不支援直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="f3332-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="f3332-122">API 名稱</span><span class="sxs-lookup"><span data-stu-id="f3332-122">API Name</span></span> |
| -------- |
| [<span data-ttu-id="f3332-123">System.Net.Connection 類別</span><span class="sxs-lookup"><span data-stu-id="f3332-123">System.Net.Connection Class</span></span>](../../../docs/framework/additional-apis/connection.md) |
| [<span data-ttu-id="f3332-124">System.Net.Connection.m\_WriteList 欄位</span><span class="sxs-lookup"><span data-stu-id="f3332-124">System.Net.Connection.m\_WriteList Field</span></span>](../../../docs/framework/additional-apis/m_writelist.md) |
| [<span data-ttu-id="f3332-125">System.Net.ConnectionGroup 類別</span><span class="sxs-lookup"><span data-stu-id="f3332-125">System.Net.ConnectionGroup Class</span></span>](../../../docs/framework/additional-apis/connectiongroup.md) |
| [<span data-ttu-id="f3332-126">System.Net.ConnectionGroup.m\_ConnectionList 欄位</span><span class="sxs-lookup"><span data-stu-id="f3332-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [<span data-ttu-id="f3332-127">System.Net.HttpWebRequest。\_HttpResponse 欄位</span><span class="sxs-lookup"><span data-stu-id="f3332-127">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](../../../docs/framework/additional-apis/_httpresponse.md) |
| [<span data-ttu-id="f3332-128">System.Net.HttpWebRequest。\_AutoRedirects 欄位</span><span class="sxs-lookup"><span data-stu-id="f3332-128">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](../../../docs/framework/additional-apis/_autoredirects.md) |
| [<span data-ttu-id="f3332-129">System.Net.ServicePoint.m\_ConnectionGroupList 欄位</span><span class="sxs-lookup"><span data-stu-id="f3332-129">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [<span data-ttu-id="f3332-130">System.Net.ServicePointManager.s\_ServicePointTable 欄位</span><span class="sxs-lookup"><span data-stu-id="f3332-130">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [<span data-ttu-id="f3332-131">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes 欄位</span><span class="sxs-lookup"><span data-stu-id="f3332-131">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="f3332-132">System.Windows.Forms.Design.DataMemberFieldEditor 類別</span><span class="sxs-lookup"><span data-stu-id="f3332-132">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [<span data-ttu-id="f3332-133">System.Windows.Forms.Design.DataMemberListEditor 類別</span><span class="sxs-lookup"><span data-stu-id="f3332-133">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="f3332-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="f3332-134">See also</span></span>

[<span data-ttu-id="f3332-135">.NET Framework 和不定期發行</span><span class="sxs-lookup"><span data-stu-id="f3332-135">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
