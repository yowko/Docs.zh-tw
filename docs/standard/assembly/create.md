---
title: 建立元件
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2dda45cca182d75bc77916cdf862ada9faead9ec
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973303"
---
# <a name="create-assemblies"></a><span data-ttu-id="d98f0-102">建立元件</span><span class="sxs-lookup"><span data-stu-id="d98f0-102">Create assemblies</span></span>

<span data-ttu-id="d98f0-103">您可以使用 IDE (例如 Visual Studio) 或 Windows SDK 所提供的編譯器與工具來建立單一檔案或多檔案組件。</span><span class="sxs-lookup"><span data-stu-id="d98f0-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows SDK.</span></span> <span data-ttu-id="d98f0-104">最簡單的組件是單一檔案，其具有簡單名稱並載入到單一應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="d98f0-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="d98f0-105">這個組件無法供應用程式目錄外部的其他組件參考，而且不會進行版本檢查。</span><span class="sxs-lookup"><span data-stu-id="d98f0-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="d98f0-106">若要解除安裝構成組件的應用程式，您只需要刪除其所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="d98f0-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="d98f0-107">對許多開發人員而言，具有這些功能的組件就是部署應用程式所需的項目。</span><span class="sxs-lookup"><span data-stu-id="d98f0-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="d98f0-108">您可以從數個程式碼模組和資源檔建立多檔案組件。</span><span class="sxs-lookup"><span data-stu-id="d98f0-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="d98f0-109">您也可以建立可供多個應用程式共用的組件。</span><span class="sxs-lookup"><span data-stu-id="d98f0-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="d98f0-110">共用組件必須有強式名稱，而且可以部署在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="d98f0-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="d98f0-111">根據下列因素，將程式碼模組和資源群組成組件時，您會有數個選項：</span><span class="sxs-lookup"><span data-stu-id="d98f0-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="d98f0-112">版本控制</span><span class="sxs-lookup"><span data-stu-id="d98f0-112">Versioning</span></span>

     <span data-ttu-id="d98f0-113">應該具有相同版本資訊的群組模組。</span><span class="sxs-lookup"><span data-stu-id="d98f0-113">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="d98f0-114">部署</span><span class="sxs-lookup"><span data-stu-id="d98f0-114">Deployment</span></span>

     <span data-ttu-id="d98f0-115">支援您部署模型的群組程式碼模組和資源。</span><span class="sxs-lookup"><span data-stu-id="d98f0-115">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="d98f0-116">重複使用</span><span class="sxs-lookup"><span data-stu-id="d98f0-116">Reuse</span></span>

     <span data-ttu-id="d98f0-117">可透過邏輯方式一起用於某個目的的群組模組。</span><span class="sxs-lookup"><span data-stu-id="d98f0-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="d98f0-118">例如，包含不常用於程式維護之類型和類別的組件可以放在相同的組件中。</span><span class="sxs-lookup"><span data-stu-id="d98f0-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="d98f0-119">此外，您想要與多個應用程式共用的類型應該群組為組件，並且應該使用強式名稱來簽署組件。</span><span class="sxs-lookup"><span data-stu-id="d98f0-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="d98f0-120">安全性</span><span class="sxs-lookup"><span data-stu-id="d98f0-120">Security</span></span>

     <span data-ttu-id="d98f0-121">包含需要相同安全性權限之類型的群組模組。</span><span class="sxs-lookup"><span data-stu-id="d98f0-121">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="d98f0-122">範圍設定</span><span class="sxs-lookup"><span data-stu-id="d98f0-122">Scoping</span></span>

     <span data-ttu-id="d98f0-123">包含其可視性應該限制為相同組件之類型的群組模組。</span><span class="sxs-lookup"><span data-stu-id="d98f0-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="d98f0-124">將 common language runtime 元件提供給未受管理的 COM 應用程式時，有一些特殊的考慮。</span><span class="sxs-lookup"><span data-stu-id="d98f0-124">There are special considerations when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="d98f0-125">如需使用非受控碼的詳細資訊，請參閱[將 .NET Framework 元件公開給 COM](../../framework/interop/exposing-dotnet-components-to-com.md)。</span><span class="sxs-lookup"><span data-stu-id="d98f0-125">For more information about working with unmanaged code, see [Expose .NET Framework components to COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d98f0-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d98f0-126">See also</span></span>

- [<span data-ttu-id="d98f0-127">具有元件的程式</span><span class="sxs-lookup"><span data-stu-id="d98f0-127">Program with assemblies</span></span>](program.md)
- [<span data-ttu-id="d98f0-128">元件版本控制</span><span class="sxs-lookup"><span data-stu-id="d98f0-128">Assembly versioning</span></span>](versioning.md)
- [<span data-ttu-id="d98f0-129">如何：建立單一檔案元件</span><span class="sxs-lookup"><span data-stu-id="d98f0-129">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)
- [<span data-ttu-id="d98f0-130">如何：建立多檔案元件</span><span class="sxs-lookup"><span data-stu-id="d98f0-130">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="d98f0-131">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="d98f0-131">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="d98f0-132">多檔案元件</span><span class="sxs-lookup"><span data-stu-id="d98f0-132">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)
