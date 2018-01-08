---
title: "部署 .NET Framework 應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying applications [.NET Framework]
- .NET Framework, deploying apps
ms.assetid: 139d4cb1-5972-40f4-bdd8-1ce68e4dfb80
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecf0a4544b5417a548c7cc212e26c98bd1891c00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-net-framework-applications"></a><span data-ttu-id="1babf-102">部署 .NET Framework 應用程式</span><span class="sxs-lookup"><span data-stu-id="1babf-102">Deploying .NET Framework Applications</span></span>
<span data-ttu-id="1babf-103">.NET Framework 文件的本章節提供部署 .NET Framework 應用程式的重要資訊，包括下列方針：載入組件、解析組件參考，以及透過產生原生映像 (NGen) 改善應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="1babf-103">This section of the .NET Framework documentation provides essential information for deploying .NET Framework applications, including guidelines for loading assemblies, resolving assembly references, and improving the performance of your application through native image generation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1babf-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="1babf-104">In This Section</span></span>  
 [<span data-ttu-id="1babf-105">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="1babf-105">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="1babf-106">說明 Common Language Runtime 如何找出並繫結至構成您應用程式的組件。</span><span class="sxs-lookup"><span data-stu-id="1babf-106">Describes how the common language runtime locates and binds to the assemblies that make up your application.</span></span>  
  
 [<span data-ttu-id="1babf-107">組件載入的最佳做法</span><span class="sxs-lookup"><span data-stu-id="1babf-107">Best Practices for Assembly Loading</span></span>](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)  
 <span data-ttu-id="1babf-108">討論如何避免發生可能造成 <xref:System.InvalidCastException>、<xref:System.MissingMethodException> 和其他錯誤之類型識別的問題。</span><span class="sxs-lookup"><span data-stu-id="1babf-108">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1babf-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="1babf-109">See Also</span></span>  
 [<span data-ttu-id="1babf-110">開發指南</span><span class="sxs-lookup"><span data-stu-id="1babf-110">Development Guide</span></span>](../../../docs/framework/development-guide.md)
