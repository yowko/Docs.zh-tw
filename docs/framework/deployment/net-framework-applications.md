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
ms.openlocfilehash: af9bacb4ba64fb4e51b6e05b3636226274c28703
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="deploying-net-framework-applications"></a><span data-ttu-id="dc85b-102">部署 .NET Framework 應用程式</span><span class="sxs-lookup"><span data-stu-id="dc85b-102">Deploying .NET Framework Applications</span></span>
<span data-ttu-id="dc85b-103">.NET Framework 文件的本章節提供部署 .NET Framework 應用程式的重要資訊，包括下列方針：載入組件、解析組件參考，以及透過產生原生映像 (NGen) 改善應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="dc85b-103">This section of the .NET Framework documentation provides essential information for deploying .NET Framework applications, including guidelines for loading assemblies, resolving assembly references, and improving the performance of your application through native image generation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc85b-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="dc85b-104">In This Section</span></span>  
 [<span data-ttu-id="dc85b-105">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="dc85b-105">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="dc85b-106">說明 Common Language Runtime 如何找出並繫結至構成您應用程式的組件。</span><span class="sxs-lookup"><span data-stu-id="dc85b-106">Describes how the common language runtime locates and binds to the assemblies that make up your application.</span></span>  
  
 [<span data-ttu-id="dc85b-107">組件載入的最佳做法</span><span class="sxs-lookup"><span data-stu-id="dc85b-107">Best Practices for Assembly Loading</span></span>](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)  
 <span data-ttu-id="dc85b-108">討論如何避免發生可能造成 <xref:System.InvalidCastException>、<xref:System.MissingMethodException> 和其他錯誤之類型識別的問題。</span><span class="sxs-lookup"><span data-stu-id="dc85b-108">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc85b-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc85b-109">See Also</span></span>  
 [<span data-ttu-id="dc85b-110">開發指南</span><span class="sxs-lookup"><span data-stu-id="dc85b-110">Development Guide</span></span>](../../../docs/framework/development-guide.md)
