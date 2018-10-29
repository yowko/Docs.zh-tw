---
title: 組件位置
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19c4b030e8b44bed5377827d016127b4a574f5ee
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50183746"
---
# <a name="assembly-location"></a><span data-ttu-id="fdff5-102">組件位置</span><span class="sxs-lookup"><span data-stu-id="fdff5-102">Assembly Location</span></span>
<span data-ttu-id="fdff5-103">組件的位置可判斷 Common Language Runtime 是否可以在參考時找到它，也可以判斷是否可以與其他組件共用組件。</span><span class="sxs-lookup"><span data-stu-id="fdff5-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="fdff5-104">您可以在下列位置中部署組件：</span><span class="sxs-lookup"><span data-stu-id="fdff5-104">You can deploy an assembly in the following locations:</span></span>  
  
-   <span data-ttu-id="fdff5-105">應用程式的目錄或子目錄。</span><span class="sxs-lookup"><span data-stu-id="fdff5-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="fdff5-106">這是部署組件的最常用位置。</span><span class="sxs-lookup"><span data-stu-id="fdff5-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="fdff5-107">應用程式根目錄的子目錄可以根據語言或文化特性。</span><span class="sxs-lookup"><span data-stu-id="fdff5-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="fdff5-108">如果組件具有文化特性屬性中的資訊，則必須在具有該文化特性名稱之應用程式目錄下的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="fdff5-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
-   <span data-ttu-id="fdff5-109">全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="fdff5-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="fdff5-110">這是只要安裝 Common Language Runtime 的位置就會安裝的全機器程式碼快取。</span><span class="sxs-lookup"><span data-stu-id="fdff5-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="fdff5-111">在大部分情況下，如果您想要與多個應用程式共用組件，則應該將它部署到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="fdff5-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="fdff5-112">在 HTTP 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="fdff5-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="fdff5-113">HTTP 伺服器上部署的組件必須具有強式名稱；您指向應用程式組態檔的程式碼基底區段中的組件。</span><span class="sxs-lookup"><span data-stu-id="fdff5-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdff5-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="fdff5-114">See Also</span></span>  
- [<span data-ttu-id="fdff5-115">建立組件</span><span class="sxs-lookup"><span data-stu-id="fdff5-115">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
- [<span data-ttu-id="fdff5-116">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="fdff5-116">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
- [<span data-ttu-id="fdff5-117">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="fdff5-117">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [<span data-ttu-id="fdff5-118">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="fdff5-118">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
