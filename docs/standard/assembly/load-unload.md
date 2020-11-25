---
title: 如何：載入和卸載元件
description: CLR 會自動載入程式所參考的 .NET 元件。 您也可以將特定的元件動態載入至目前的應用程式域。
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: fe1a5fe63361620f8ab99ec8469169ed2213c0ee
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731484"
---
# <a name="how-to-load-and-unload-assemblies"></a><span data-ttu-id="7854e-104">如何：載入和卸載元件</span><span class="sxs-lookup"><span data-stu-id="7854e-104">How to: Load and unload assemblies</span></span>

<span data-ttu-id="7854e-105">Common language runtime 會自動載入程式所參考的元件，但也可以將特定的元件動態載入至目前的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="7854e-105">The assemblies referenced by your program will automatically be loaded by the common language runtime, but it is also possible to dynamically load specific assemblies into the current application domain.</span></span> <span data-ttu-id="7854e-106">如需詳細資訊，請參閱 [如何：將元件載入應用程式域](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="7854e-106">For more information, see [How to: Load assemblies into an application domain](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>

<span data-ttu-id="7854e-107">在 .NET Framework 中，沒有任何方法可卸載個別的元件，而不需要卸載所有包含該元件的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="7854e-107">In .NET Framework, there is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="7854e-108">即使組件超出範圍，實際組件檔仍會保持載入狀態，直到卸載所有包含該組件的應用程式定義域為止。</span><span class="sxs-lookup"><span data-stu-id="7854e-108">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span> <span data-ttu-id="7854e-109">在 .NET Core 中， <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> 類別會處理元件的卸載。</span><span class="sxs-lookup"><span data-stu-id="7854e-109">In .NET Core, the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> class handles the unloading of assemblies.</span></span> <span data-ttu-id="7854e-110">如需詳細資訊，請參閱 [如何在 .Net Core 中使用和偵錯工具集卸載功能](unloadability.md)。</span><span class="sxs-lookup"><span data-stu-id="7854e-110">For more information, see [How to use and debug assembly unloadability in .NET Core](unloadability.md).</span></span>

## <a name="load-and-unload-assemblies"></a><span data-ttu-id="7854e-111">載入和卸載組件</span><span class="sxs-lookup"><span data-stu-id="7854e-111">Load and unload assemblies</span></span>

<span data-ttu-id="7854e-112">若要將元件載入應用程式域，請使用類別和中包含的數個載入方法 <xref:System.AppDomain> 之一 <xref:System.Reflection.Assembly> 。</span><span class="sxs-lookup"><span data-stu-id="7854e-112">To load an assembly into an application domain, use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection.Assembly>.</span></span> <span data-ttu-id="7854e-113">如需詳細資訊，請參閱 [如何：將元件載入應用程式域](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="7854e-113">For more information, see [How to: Load assemblies into an application domain](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span> <span data-ttu-id="7854e-114">請注意，.NET Core 僅支援單一應用程式域。</span><span class="sxs-lookup"><span data-stu-id="7854e-114">Note that .NET Core supports only a single application domain.</span></span>

<span data-ttu-id="7854e-115">若要卸載 .NET Framework 中的元件，您必須卸載所有包含該元件的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="7854e-115">To unload an assembly in the .NET Framework, you must unload all of the application domains that contain it.</span></span> <span data-ttu-id="7854e-116">若要卸載應用程式域，請使用 <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="7854e-116">To unload an application domain, use the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7854e-117">如需詳細資訊，請參閱 [如何：卸載應用程式域](../../framework/app-domains/how-to-unload-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="7854e-117">For more information, see [How to: Unload an application domain](../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>

<span data-ttu-id="7854e-118">如果您想要卸載某些元件，而不是 .NET Framework 應用程式中的其他元件，請考慮建立新的應用程式域、在該網域內執行程式碼，然後再卸載該應用程式域。</span><span class="sxs-lookup"><span data-stu-id="7854e-118">If you want to unload some assemblies but not others in a .NET Framework application, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="7854e-119">如需詳細資訊，請參閱 [如何：卸載應用程式域](../../framework/app-domains/how-to-unload-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="7854e-119">For more information, see [How to: Unload an application domain](../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="7854e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7854e-120">See also</span></span>

- [<span data-ttu-id="7854e-121">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="7854e-121">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7854e-122"> (Visual Basic) 的程式設計概念 </span><span class="sxs-lookup"><span data-stu-id="7854e-122">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="7854e-123">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="7854e-123">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="7854e-124">如何：將元件載入應用程式域</span><span class="sxs-lookup"><span data-stu-id="7854e-124">How to: Load assemblies into an application domain</span></span>](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
