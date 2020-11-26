---
title: 部署 .NET Framework 應用程式
description: 開始部署 .NET 應用程式。 請參閱 common language runtime 如何找出元件的相關文章，以及元件載入的最佳做法。
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework]
- .NET Framework, deploying apps
ms.assetid: 139d4cb1-5972-40f4-bdd8-1ce68e4dfb80
ms.openlocfilehash: 3ede6f8aba00bd4ea3e7326eade7b51a9c9a867f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240377"
---
# <a name="deploying-net-framework-applications"></a><span data-ttu-id="a3593-104">部署 .NET Framework 應用程式</span><span class="sxs-lookup"><span data-stu-id="a3593-104">Deploying .NET Framework Applications</span></span>

<span data-ttu-id="a3593-105">.NET Framework 文件的本章節提供部署 .NET Framework 應用程式的重要資訊，包括下列方針：載入組件、解析組件參考，以及透過產生原生映像 (NGen) 改善應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="a3593-105">This section of the .NET Framework documentation provides essential information for deploying .NET Framework applications, including guidelines for loading assemblies, resolving assembly references, and improving the performance of your application through native image generation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a3593-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="a3593-106">In This Section</span></span>  

 [<span data-ttu-id="a3593-107">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="a3593-107">How the Runtime Locates Assemblies</span></span>](how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="a3593-108">說明 Common Language Runtime 如何找出並繫結至構成您應用程式的組件。</span><span class="sxs-lookup"><span data-stu-id="a3593-108">Describes how the common language runtime locates and binds to the assemblies that make up your application.</span></span>  
  
 [<span data-ttu-id="a3593-109">組件載入的最佳作法</span><span class="sxs-lookup"><span data-stu-id="a3593-109">Best Practices for Assembly Loading</span></span>](best-practices-for-assembly-loading.md)  
 <span data-ttu-id="a3593-110">討論如何避免發生可能造成 <xref:System.InvalidCastException>、<xref:System.MissingMethodException> 和其他錯誤之類型識別的問題。</span><span class="sxs-lookup"><span data-stu-id="a3593-110">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3593-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3593-111">See also</span></span>

- [<span data-ttu-id="a3593-112">開發指南</span><span class="sxs-lookup"><span data-stu-id="a3593-112">Development Guide</span></span>](../development-guide.md)
