---
title: 建立組件
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e544976b0b801b08af238b2aeb36b5611154379
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832905"
---
# <a name="creating-assemblies"></a><span data-ttu-id="3d553-102">建立組件</span><span class="sxs-lookup"><span data-stu-id="3d553-102">Creating Assemblies</span></span>

<span data-ttu-id="3d553-103">您可以使用 IDE (例如 Visual Studio) 或 Windows 軟體開發套件 (SDK) 所提供的編譯器和工具來建立單一檔案或多檔案組件。</span><span class="sxs-lookup"><span data-stu-id="3d553-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows Software Development Kit (SDK).</span></span> <span data-ttu-id="3d553-104">最簡單的組件是單一檔案，其具有簡單名稱並載入到單一應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="3d553-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="3d553-105">這個組件無法供應用程式目錄外部的其他組件參考，而且不會進行版本檢查。</span><span class="sxs-lookup"><span data-stu-id="3d553-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="3d553-106">若要解除安裝構成組件的應用程式，您只需要刪除其所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="3d553-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="3d553-107">對許多開發人員而言，具有這些功能的組件就是部署應用程式所需的項目。</span><span class="sxs-lookup"><span data-stu-id="3d553-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="3d553-108">您可以從數個程式碼模組和資源檔建立多檔案組件。</span><span class="sxs-lookup"><span data-stu-id="3d553-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="3d553-109">您也可以建立可供多個應用程式共用的組件。</span><span class="sxs-lookup"><span data-stu-id="3d553-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="3d553-110">共用組件必須有強式名稱，而且可以部署在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="3d553-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="3d553-111">根據下列因素，將程式碼模組和資源群組成組件時，您會有數個選項：</span><span class="sxs-lookup"><span data-stu-id="3d553-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="3d553-112">版本控制</span><span class="sxs-lookup"><span data-stu-id="3d553-112">Versioning</span></span>

     <span data-ttu-id="3d553-113">應該具有相同版本資訊的群組模組。</span><span class="sxs-lookup"><span data-stu-id="3d553-113">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="3d553-114">部署</span><span class="sxs-lookup"><span data-stu-id="3d553-114">Deployment</span></span>

     <span data-ttu-id="3d553-115">支援您部署模型的群組程式碼模組和資源。</span><span class="sxs-lookup"><span data-stu-id="3d553-115">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="3d553-116">重複使用</span><span class="sxs-lookup"><span data-stu-id="3d553-116">Reuse</span></span>

     <span data-ttu-id="3d553-117">可透過邏輯方式一起用於某個目的的群組模組。</span><span class="sxs-lookup"><span data-stu-id="3d553-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="3d553-118">例如，包含不常用於程式維護之類型和類別的組件可以放在相同的組件中。</span><span class="sxs-lookup"><span data-stu-id="3d553-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="3d553-119">此外，您想要與多個應用程式共用的類型應該群組為組件，並且應該使用強式名稱來簽署組件。</span><span class="sxs-lookup"><span data-stu-id="3d553-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="3d553-120">安全性</span><span class="sxs-lookup"><span data-stu-id="3d553-120">Security</span></span>

     <span data-ttu-id="3d553-121">包含需要相同安全性權限之類型的群組模組。</span><span class="sxs-lookup"><span data-stu-id="3d553-121">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="3d553-122">範圍設定</span><span class="sxs-lookup"><span data-stu-id="3d553-122">Scoping</span></span>

     <span data-ttu-id="3d553-123">包含其可視性應該限制為相同組件之類型的群組模組。</span><span class="sxs-lookup"><span data-stu-id="3d553-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="3d553-124">讓 Unmanaged COM 應用程式使用 Common Language Runtime 組件時，必須進行特殊考量。</span><span class="sxs-lookup"><span data-stu-id="3d553-124">Special considerations must be made when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="3d553-125">如需使用 Unmanaged 程式碼的詳細資訊，請參閱[將 .NET Framework 元件公開給 COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)。</span><span class="sxs-lookup"><span data-stu-id="3d553-125">For more information about working with unmanaged code, see [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d553-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d553-126">See also</span></span>

- [<span data-ttu-id="3d553-127">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="3d553-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="3d553-128">組件版本控制</span><span class="sxs-lookup"><span data-stu-id="3d553-128">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)
- [<span data-ttu-id="3d553-129">如何：建置單一檔案組件</span><span class="sxs-lookup"><span data-stu-id="3d553-129">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)
- [<span data-ttu-id="3d553-130">如何：建置多檔案組件</span><span class="sxs-lookup"><span data-stu-id="3d553-130">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="3d553-131">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="3d553-131">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="3d553-132">多檔案組件</span><span class="sxs-lookup"><span data-stu-id="3d553-132">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
