---
title: 組件位置
description: .NET 元件的位置會決定 CLR 如何尋找它，以及是否可以與其他元件共用。
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 1fa1c486c0cddce4ddcfae7f2df27e2e85c88e66
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687603"
---
# <a name="assembly-location"></a><span data-ttu-id="84035-103">組件位置</span><span class="sxs-lookup"><span data-stu-id="84035-103">Assembly location</span></span>

<span data-ttu-id="84035-104">組件的位置可判斷 Common Language Runtime 是否可以在參考時找到它，也可以判斷是否可以與其他組件共用組件。</span><span class="sxs-lookup"><span data-stu-id="84035-104">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="84035-105">您可以在下列位置中部署組件：</span><span class="sxs-lookup"><span data-stu-id="84035-105">You can deploy an assembly in the following locations:</span></span>

- <span data-ttu-id="84035-106">應用程式的目錄或子目錄。</span><span class="sxs-lookup"><span data-stu-id="84035-106">The application's directory or subdirectories.</span></span>

     <span data-ttu-id="84035-107">這是部署組件的最常用位置。</span><span class="sxs-lookup"><span data-stu-id="84035-107">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="84035-108">應用程式根目錄的子目錄可以根據語言或文化特性。</span><span class="sxs-lookup"><span data-stu-id="84035-108">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="84035-109">如果組件具有文化特性屬性中的資訊，則必須在具有該文化特性名稱之應用程式目錄下的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="84035-109">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>

- <span data-ttu-id="84035-110">全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="84035-110">The global assembly cache.</span></span>

     <span data-ttu-id="84035-111">這是只要安裝 Common Language Runtime 的位置就會安裝的全機器程式碼快取。</span><span class="sxs-lookup"><span data-stu-id="84035-111">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="84035-112">在大部分情況下，如果您想要與多個應用程式共用組件，則應該將它部署到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="84035-112">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>

- <span data-ttu-id="84035-113">在 HTTP 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="84035-113">On an HTTP server.</span></span>

     <span data-ttu-id="84035-114">HTTP 伺服器上部署的組件必須具有強式名稱；您指向應用程式組態檔的程式碼基底區段中的組件。</span><span class="sxs-lookup"><span data-stu-id="84035-114">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="84035-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="84035-115">See also</span></span>

- [<span data-ttu-id="84035-116">建立組件</span><span class="sxs-lookup"><span data-stu-id="84035-116">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="84035-117">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="84035-117">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="84035-118">執行時間如何找出元件</span><span class="sxs-lookup"><span data-stu-id="84035-118">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
