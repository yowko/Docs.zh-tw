---
title: 匯入類型程式庫做為組件
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- type metadata
- custom wrappers
- metadata
- exposing COM components to .NET Framework
- Type Library Importer
- interoperation with unmanaged code, importing type library
- interoperation with unmanaged code, exposing COM components
- type libraries
- TypeLibConverter class, importing type library as assembly
- COM interop, importing type library
- COM interop, exposing COM components
ms.assetid: d1898229-cd40-426e-a275-f3eb65fbc79f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db9571a2d07bcdf9830ef93cd07a5dae912f4677
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051713"
---
# <a name="importing-a-type-library-as-an-assembly"></a><span data-ttu-id="74299-102">匯入類型程式庫做為組件</span><span class="sxs-lookup"><span data-stu-id="74299-102">Importing a Type Library as an Assembly</span></span>

<span data-ttu-id="74299-103">COM 類型定義通常位於型別程式庫中。</span><span class="sxs-lookup"><span data-stu-id="74299-103">COM type definitions usually reside in a type library.</span></span> <span data-ttu-id="74299-104">反之，符合 CLS 的編譯器則是在組件中產生型別中繼資料。</span><span class="sxs-lookup"><span data-stu-id="74299-104">In contrast, CLS-compliant compilers produce type metadata in an assembly.</span></span> <span data-ttu-id="74299-105">這兩種類型資訊的來源有相當大的差異。</span><span class="sxs-lookup"><span data-stu-id="74299-105">The two sources of type information are quite different.</span></span> <span data-ttu-id="74299-106">本主題描述從型別程式庫產生中繼資料的技術。</span><span class="sxs-lookup"><span data-stu-id="74299-106">This topic describes techniques for generating metadata from a type library.</span></span> <span data-ttu-id="74299-107">產生的組件稱為 Interop 組件，其包含的類型資訊可讓 .NET Framework 應用程式使用 COM 類型。</span><span class="sxs-lookup"><span data-stu-id="74299-107">The resulting assembly is called an interop assembly, and the type information it contains enables .NET Framework applications to use COM types.</span></span>

<span data-ttu-id="74299-108">有兩種方式可讓此類型資訊能夠用於應用程式中：</span><span class="sxs-lookup"><span data-stu-id="74299-108">There are two ways to make this type information available to your application:</span></span>

- <span data-ttu-id="74299-109">使用僅限設計階段的 Interop 組件：從 .NET Framework 4 開始，您可以指示編譯器將 Interop 組件的類型資訊內嵌到可執行檔。</span><span class="sxs-lookup"><span data-stu-id="74299-109">Using design-time-only interop assemblies: Beginning with the .NET Framework 4, you can instruct the compiler to embed type information from the interop assembly into your executable.</span></span> <span data-ttu-id="74299-110">編譯器只會內嵌應用程式使用的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="74299-110">The compiler embeds only the type information that your application uses.</span></span> <span data-ttu-id="74299-111">您不必與應用程式一起部署 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="74299-111">You do not have to deploy the interop assembly with your application.</span></span> <span data-ttu-id="74299-112">這是建議使用的技巧。</span><span class="sxs-lookup"><span data-stu-id="74299-112">This is the recommended technique.</span></span>

- <span data-ttu-id="74299-113">部署 Interop 組件：您可以建立 Interop 組件的標準參考。</span><span class="sxs-lookup"><span data-stu-id="74299-113">Deploying interop assemblies: You can create a standard reference to the interop assembly.</span></span> <span data-ttu-id="74299-114">在此情況下，Interop 組件必須與您的應用程式一起部署。</span><span class="sxs-lookup"><span data-stu-id="74299-114">In this case, the interop assembly must be deployed with your application.</span></span> <span data-ttu-id="74299-115">如果您運用這項技巧，但不使用私用的 COM 元件，請一律參考 COM 元件作者發佈的主要 Interop 組件 (PIA)，這是您想要併入 Managed 程式碼的 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="74299-115">If you employ this technique, and you are not using a private COM component, always reference the primary interop assembly (PIA) published by the author of the COM component you intend to incorporate in your managed code.</span></span> <span data-ttu-id="74299-116">如需產生和使用主要 Interop 組件的詳細資訊，請參閱[主要 Interop 組件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="74299-116">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).</span></span>

<span data-ttu-id="74299-117">當您使用僅限設計階段的 Interop 組件時，可以內嵌 COM 元件作者所發佈之主要 Interop 組件的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="74299-117">When you use design-time-only interop assemblies, you can embed type information from the primary interop assembly published by the author of the COM component.</span></span> <span data-ttu-id="74299-118">不過，您不必與應用程式一起部署主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="74299-118">However, you do not have to deploy the primary interop assembly with your application.</span></span>

<span data-ttu-id="74299-119">使用僅限設計階段 Interop 組件會減少應用程式的大小，因為大部分的應用程式不會使用 COM 元件的所有功能。</span><span class="sxs-lookup"><span data-stu-id="74299-119">Using design-time-only interop assemblies reduces the size of your application, because most applications do not use all the features of a COM component.</span></span> <span data-ttu-id="74299-120">編譯器在內嵌類型資訊時非常有效；如果應用程式只使用 COM 介面的部分方法，則編譯器不會內嵌未使用的方法。</span><span class="sxs-lookup"><span data-stu-id="74299-120">The compiler is very efficient when it embeds type information; if your application uses only some of the methods on a COM interface, the compiler does not embed the unused methods.</span></span> <span data-ttu-id="74299-121">當具有內嵌類型資訊的應用程式與其他此類應用程式互動，或與使用主要 Interop 組件的應用程式互動時，通用語言執行平台會使用類型相等規則，來判斷兩個類型是否使用相同的名稱表示相同的 COM 類型。</span><span class="sxs-lookup"><span data-stu-id="74299-121">When an application that has embedded type information interacts with another such application, or interacts with an application that uses a primary interop assembly, the common language runtime uses type equivalence rules to determine whether two types with the same name represent the same COM type.</span></span> <span data-ttu-id="74299-122">您不需要知道這些規則，就可使用 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="74299-122">You do not have to know these rules to use COM objects.</span></span> <span data-ttu-id="74299-123">不過，如果對這些規則感興趣，請參閱[類型相等和內嵌 Interop 類型](type-equivalence-and-embedded-interop-types.md)。</span><span class="sxs-lookup"><span data-stu-id="74299-123">However, if you are interested in the rules, see [Type Equivalence and Embedded Interop Types](type-equivalence-and-embedded-interop-types.md).</span></span>

## <a name="generating-metadata"></a><span data-ttu-id="74299-124">產生中繼資料</span><span class="sxs-lookup"><span data-stu-id="74299-124">Generating Metadata</span></span>

<span data-ttu-id="74299-125">COM 類型程式庫可以是單獨的檔案，副檔名為 .tlb (例如 Loanlib.tlb)。</span><span class="sxs-lookup"><span data-stu-id="74299-125">COM type libraries can be stand-alone files that have a .tlb extension, such as Loanlib.tlb.</span></span> <span data-ttu-id="74299-126">有些型別程式庫則會嵌入在 .dll 或 .exe 檔案的資源區段中。</span><span class="sxs-lookup"><span data-stu-id="74299-126">Some type libraries are embedded in the resource section of a .dll or .exe file.</span></span> <span data-ttu-id="74299-127">型別程式庫資訊的其他來源為 .olb 和 .ocx 檔案。</span><span class="sxs-lookup"><span data-stu-id="74299-127">Other sources of type library information are .olb and .ocx files.</span></span>

<span data-ttu-id="74299-128">找到包含目標 COM 類型實作的型別程式庫之後，您可以使用下列選項，產生包含類型中繼資料的 Interop 組件：</span><span class="sxs-lookup"><span data-stu-id="74299-128">After you locate the type library that contains the implementation of your target COM type, you have the following options for generating an interop assembly containing type metadata:</span></span>

- <span data-ttu-id="74299-129">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="74299-129">Visual Studio</span></span>

  <span data-ttu-id="74299-130">Visual Studio 會自動將型別程式庫中的 COM 類型轉換為組件中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="74299-130">Visual Studio automatically converts COM types in a type library to metadata in an assembly.</span></span> <span data-ttu-id="74299-131">如需相關指示，請參閱[如何：將參考新增至類型程式庫](how-to-add-references-to-type-libraries.md)。</span><span class="sxs-lookup"><span data-stu-id="74299-131">For instructions, see [How to: Add References to Type Libraries](how-to-add-references-to-type-libraries.md).</span></span>

- [<span data-ttu-id="74299-132">型別程式庫匯入工具 (Tlbimp.exe)</span><span class="sxs-lookup"><span data-stu-id="74299-132">Type Library Importer (Tlbimp.exe)</span></span>](../tools/tlbimp-exe-type-library-importer.md)

  <span data-ttu-id="74299-133">型別程式庫匯入工具提供命令列選項，可以調整產生的 Interop 檔案的中繼資料、從現有型別程式庫匯入型別，以及產生 Interop 組件和命名空間。</span><span class="sxs-lookup"><span data-stu-id="74299-133">The Type Library Importer provides command-line options to adjust metadata in the resulting interop file, imports types from an existing type library, and generates an interop assembly and a namespace.</span></span> <span data-ttu-id="74299-134">如需相關指示，請參閱[如何：從型別程式庫產生 Interop 組件](how-to-generate-interop-assemblies-from-type-libraries.md)。</span><span class="sxs-lookup"><span data-stu-id="74299-134">For instructions, see [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>

- <span data-ttu-id="74299-135"><xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="74299-135"><xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> class</span></span>

  <span data-ttu-id="74299-136">這個類別提供將型別程式庫中的 coclass 和介面轉換為組件內中繼資料的方法。</span><span class="sxs-lookup"><span data-stu-id="74299-136">This class provides methods to convert coclasses and interfaces in a type library to metadata within an assembly.</span></span> <span data-ttu-id="74299-137">它會產生與 Tlbimp.exe 相同的中繼資料輸出。</span><span class="sxs-lookup"><span data-stu-id="74299-137">It produces the same metadata output as Tlbimp.exe.</span></span> <span data-ttu-id="74299-138">不過，不同於 Tlbimp.exe，<xref:System.Runtime.InteropServices.TypeLibConverter> 類別可以將記憶體內部型別程式庫轉換為中繼資料。</span><span class="sxs-lookup"><span data-stu-id="74299-138">However, unlike Tlbimp.exe, the <xref:System.Runtime.InteropServices.TypeLibConverter> class can convert an in-memory type library to metadata.</span></span>

- <span data-ttu-id="74299-139">自訂包裝函式</span><span class="sxs-lookup"><span data-stu-id="74299-139">Custom wrappers</span></span>

  <span data-ttu-id="74299-140">當型別程式庫無法使用或不正確時，其中一項選擇就是在 Managed 原始程式碼中建立類別或介面的重複定義。</span><span class="sxs-lookup"><span data-stu-id="74299-140">When a type library is unavailable or incorrect, one option is to create a duplicate definition of the class or interface in managed source code.</span></span> <span data-ttu-id="74299-141">然後，您可以使用以執行階段為目標的編譯器編譯這個原始程式碼，以產生組件中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="74299-141">You then compile the source code with a compiler that targets the runtime to produce metadata in an assembly.</span></span>

  <span data-ttu-id="74299-142">若要以手動方式定義 COM 類型，您必須擁有下列項目的存取權：</span><span class="sxs-lookup"><span data-stu-id="74299-142">To define COM types manually, you must have access to the following items:</span></span>

  - <span data-ttu-id="74299-143">要定義的 coclass 和介面的精確描述。</span><span class="sxs-lookup"><span data-stu-id="74299-143">Precise descriptions of the coclasses and interfaces being defined.</span></span>

  - <span data-ttu-id="74299-144">可產生適當 .NET Framework 類別定義的編譯器，例如 C# 編譯器。</span><span class="sxs-lookup"><span data-stu-id="74299-144">A compiler, such as the C# compiler, that can generate the appropriate .NET Framework class definitions.</span></span>

  - <span data-ttu-id="74299-145">型別程式庫轉換為組件的轉換規則知識。</span><span class="sxs-lookup"><span data-stu-id="74299-145">Knowledge of the type library-to-assembly conversion rules.</span></span>

  <span data-ttu-id="74299-146">撰寫自訂包裝函式是進階技術。</span><span class="sxs-lookup"><span data-stu-id="74299-146">Writing a custom wrapper is an advanced technique.</span></span> <span data-ttu-id="74299-147">如需如何產生自訂包裝函式的詳細資訊，請參閱[自訂標準包裝函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="74299-147">For additional information about how to generate a custom wrapper, see [Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100)).</span></span>

 <span data-ttu-id="74299-148">如需 COM Interop 匯入處理序的詳細資訊，請參閱[型別程式庫至組件轉換的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="74299-148">For more information about the COM interop import process, see [Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="74299-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74299-149">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- [<span data-ttu-id="74299-150">將 COM 元件公開給 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="74299-150">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- <span data-ttu-id="74299-151">[型別程式庫至組件轉換的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="74299-151">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>
- [<span data-ttu-id="74299-152">Tlbimp.exe (類型程式庫匯入工具)</span><span class="sxs-lookup"><span data-stu-id="74299-152">Tlbimp.exe (Type Library Importer)</span></span>](../tools/tlbimp-exe-type-library-importer.md)
- <span data-ttu-id="74299-153">[自訂標準包裝函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="74299-153">[Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="74299-154">[在受控程式碼中使用 COM 類型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="74299-154">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="74299-155">編譯 Interop 專案</span><span class="sxs-lookup"><span data-stu-id="74299-155">Compiling an Interop Project</span></span>](compiling-an-interop-project.md)
- [<span data-ttu-id="74299-156">部署 Interop 應用程式</span><span class="sxs-lookup"><span data-stu-id="74299-156">Deploying an Interop Application</span></span>](deploying-an-interop-application.md)
- [<span data-ttu-id="74299-157">如何：將參考新增至型別程式庫</span><span class="sxs-lookup"><span data-stu-id="74299-157">How to: Add References to Type Libraries</span></span>](how-to-add-references-to-type-libraries.md)
- [<span data-ttu-id="74299-158">如何：從型別程式庫產生 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="74299-158">How to: Generate Interop Assemblies from Type Libraries</span></span>](how-to-generate-interop-assemblies-from-type-libraries.md)
