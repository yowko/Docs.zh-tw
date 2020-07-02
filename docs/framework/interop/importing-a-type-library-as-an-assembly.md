---
title: 匯入類型程式庫做為組件
description: 匯入類型程式庫（其中包含 COM 類型定義）做為元件。 瞭解從型別程式庫建立中繼資料的方式，產生 interop 元件。
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
ms.openlocfilehash: e5187e3c2ce533f25a38e93bc3715dd3e2e47c11
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622714"
---
# <a name="importing-a-type-library-as-an-assembly"></a><span data-ttu-id="0278d-104">匯入類型程式庫做為組件</span><span class="sxs-lookup"><span data-stu-id="0278d-104">Importing a Type Library as an Assembly</span></span>

<span data-ttu-id="0278d-105">COM 類型定義通常位於型別程式庫中。</span><span class="sxs-lookup"><span data-stu-id="0278d-105">COM type definitions usually reside in a type library.</span></span> <span data-ttu-id="0278d-106">反之，符合 CLS 的編譯器則是在組件中產生型別中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0278d-106">In contrast, CLS-compliant compilers produce type metadata in an assembly.</span></span> <span data-ttu-id="0278d-107">這兩種類型資訊的來源有相當大的差異。</span><span class="sxs-lookup"><span data-stu-id="0278d-107">The two sources of type information are quite different.</span></span> <span data-ttu-id="0278d-108">本主題描述從型別程式庫產生中繼資料的技術。</span><span class="sxs-lookup"><span data-stu-id="0278d-108">This topic describes techniques for generating metadata from a type library.</span></span> <span data-ttu-id="0278d-109">產生的組件稱為 Interop 組件，其包含的類型資訊可讓 .NET Framework 應用程式使用 COM 類型。</span><span class="sxs-lookup"><span data-stu-id="0278d-109">The resulting assembly is called an interop assembly, and the type information it contains enables .NET Framework applications to use COM types.</span></span>

<span data-ttu-id="0278d-110">有兩種方式可讓此類型資訊能夠用於應用程式中：</span><span class="sxs-lookup"><span data-stu-id="0278d-110">There are two ways to make this type information available to your application:</span></span>

- <span data-ttu-id="0278d-111">使用僅限設計階段的 interop 元件：從 .NET Framework 4 開始，您可以指示編譯器將 interop 元件的類型資訊內嵌到可執行檔。</span><span class="sxs-lookup"><span data-stu-id="0278d-111">Using design-time-only interop assemblies: Beginning with the .NET Framework 4, you can instruct the compiler to embed type information from the interop assembly into your executable.</span></span> <span data-ttu-id="0278d-112">編譯器只會內嵌應用程式使用的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="0278d-112">The compiler embeds only the type information that your application uses.</span></span> <span data-ttu-id="0278d-113">您不必與應用程式一起部署 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="0278d-113">You do not have to deploy the interop assembly with your application.</span></span> <span data-ttu-id="0278d-114">這是建議使用的技巧。</span><span class="sxs-lookup"><span data-stu-id="0278d-114">This is the recommended technique.</span></span>

- <span data-ttu-id="0278d-115">部署 Interop 組件：您可以建立 Interop 組件的標準參考。</span><span class="sxs-lookup"><span data-stu-id="0278d-115">Deploying interop assemblies: You can create a standard reference to the interop assembly.</span></span> <span data-ttu-id="0278d-116">在此情況下，Interop 組件必須與您的應用程式一起部署。</span><span class="sxs-lookup"><span data-stu-id="0278d-116">In this case, the interop assembly must be deployed with your application.</span></span> <span data-ttu-id="0278d-117">如果您運用這項技巧，但不使用私用的 COM 元件，請一律參考 COM 元件作者發佈的主要 Interop 組件 (PIA)，這是您想要併入 Managed 程式碼的 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="0278d-117">If you employ this technique, and you are not using a private COM component, always reference the primary interop assembly (PIA) published by the author of the COM component you intend to incorporate in your managed code.</span></span> <span data-ttu-id="0278d-118">如需產生和使用主要 Interop 組件的詳細資訊，請參閱[主要 Interop 組件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="0278d-118">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).</span></span>

<span data-ttu-id="0278d-119">當您使用僅限設計階段的 Interop 組件時，可以內嵌 COM 元件作者所發佈之主要 Interop 組件的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="0278d-119">When you use design-time-only interop assemblies, you can embed type information from the primary interop assembly published by the author of the COM component.</span></span> <span data-ttu-id="0278d-120">不過，您不必與應用程式一起部署主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="0278d-120">However, you do not have to deploy the primary interop assembly with your application.</span></span>

<span data-ttu-id="0278d-121">使用僅限設計階段 Interop 組件會減少應用程式的大小，因為大部分的應用程式不會使用 COM 元件的所有功能。</span><span class="sxs-lookup"><span data-stu-id="0278d-121">Using design-time-only interop assemblies reduces the size of your application, because most applications do not use all the features of a COM component.</span></span> <span data-ttu-id="0278d-122">編譯器在內嵌類型資訊時非常有效；如果應用程式只使用 COM 介面的部分方法，則編譯器不會內嵌未使用的方法。</span><span class="sxs-lookup"><span data-stu-id="0278d-122">The compiler is very efficient when it embeds type information; if your application uses only some of the methods on a COM interface, the compiler does not embed the unused methods.</span></span> <span data-ttu-id="0278d-123">當具有內嵌類型資訊的應用程式與其他此類應用程式互動，或與使用主要 Interop 組件的應用程式互動時，通用語言執行平台會使用類型相等規則，來判斷兩個類型是否使用相同的名稱表示相同的 COM 類型。</span><span class="sxs-lookup"><span data-stu-id="0278d-123">When an application that has embedded type information interacts with another such application, or interacts with an application that uses a primary interop assembly, the common language runtime uses type equivalence rules to determine whether two types with the same name represent the same COM type.</span></span> <span data-ttu-id="0278d-124">您不需要知道這些規則，就可使用 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="0278d-124">You do not have to know these rules to use COM objects.</span></span> <span data-ttu-id="0278d-125">不過，如果對這些規則感興趣，請參閱[類型相等和內嵌 Interop 類型](type-equivalence-and-embedded-interop-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0278d-125">However, if you are interested in the rules, see [Type Equivalence and Embedded Interop Types](type-equivalence-and-embedded-interop-types.md).</span></span>

## <a name="generating-metadata"></a><span data-ttu-id="0278d-126">產生中繼資料</span><span class="sxs-lookup"><span data-stu-id="0278d-126">Generating Metadata</span></span>

<span data-ttu-id="0278d-127">COM 類型程式庫可以是單獨的檔案，副檔名為 .tlb (例如 Loanlib.tlb)。</span><span class="sxs-lookup"><span data-stu-id="0278d-127">COM type libraries can be stand-alone files that have a .tlb extension, such as Loanlib.tlb.</span></span> <span data-ttu-id="0278d-128">有些型別程式庫則會嵌入在 .dll 或 .exe 檔案的資源區段中。</span><span class="sxs-lookup"><span data-stu-id="0278d-128">Some type libraries are embedded in the resource section of a .dll or .exe file.</span></span> <span data-ttu-id="0278d-129">型別程式庫資訊的其他來源為 .olb 和 .ocx 檔案。</span><span class="sxs-lookup"><span data-stu-id="0278d-129">Other sources of type library information are .olb and .ocx files.</span></span>

<span data-ttu-id="0278d-130">找到包含目標 COM 類型實作的型別程式庫之後，您可以使用下列選項，產生包含類型中繼資料的 Interop 組件：</span><span class="sxs-lookup"><span data-stu-id="0278d-130">After you locate the type library that contains the implementation of your target COM type, you have the following options for generating an interop assembly containing type metadata:</span></span>

- <span data-ttu-id="0278d-131">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0278d-131">Visual Studio</span></span>

  <span data-ttu-id="0278d-132">Visual Studio 會自動將型別程式庫中的 COM 類型轉換為組件中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0278d-132">Visual Studio automatically converts COM types in a type library to metadata in an assembly.</span></span> <span data-ttu-id="0278d-133">如需指示，請參閱[如何：將參考加入至類型程式庫](how-to-add-references-to-type-libraries.md)。</span><span class="sxs-lookup"><span data-stu-id="0278d-133">For instructions, see [How to: Add References to Type Libraries](how-to-add-references-to-type-libraries.md).</span></span>

- [<span data-ttu-id="0278d-134">型別程式庫匯入工具 (Tlbimp.exe)</span><span class="sxs-lookup"><span data-stu-id="0278d-134">Type Library Importer (Tlbimp.exe)</span></span>](../tools/tlbimp-exe-type-library-importer.md)

  <span data-ttu-id="0278d-135">型別程式庫匯入工具提供命令列選項，可以調整產生的 Interop 檔案的中繼資料、從現有型別程式庫匯入型別，以及產生 Interop 組件和命名空間。</span><span class="sxs-lookup"><span data-stu-id="0278d-135">The Type Library Importer provides command-line options to adjust metadata in the resulting interop file, imports types from an existing type library, and generates an interop assembly and a namespace.</span></span> <span data-ttu-id="0278d-136">如需指示，請參閱[何：從型別程式庫產生 Interop 組件](how-to-generate-interop-assemblies-from-type-libraries.md)。</span><span class="sxs-lookup"><span data-stu-id="0278d-136">For instructions, see [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>

- <span data-ttu-id="0278d-137"><xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> 類別</span><span class="sxs-lookup"><span data-stu-id="0278d-137"><xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> class</span></span>

  <span data-ttu-id="0278d-138">這個類別提供將型別程式庫中的 coclass 和介面轉換為組件內中繼資料的方法。</span><span class="sxs-lookup"><span data-stu-id="0278d-138">This class provides methods to convert coclasses and interfaces in a type library to metadata within an assembly.</span></span> <span data-ttu-id="0278d-139">它會產生與 Tlbimp.exe 相同的中繼資料輸出。</span><span class="sxs-lookup"><span data-stu-id="0278d-139">It produces the same metadata output as Tlbimp.exe.</span></span> <span data-ttu-id="0278d-140">不過，不同於 Tlbimp.exe，<xref:System.Runtime.InteropServices.TypeLibConverter> 類別可以將記憶體內部型別程式庫轉換為中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0278d-140">However, unlike Tlbimp.exe, the <xref:System.Runtime.InteropServices.TypeLibConverter> class can convert an in-memory type library to metadata.</span></span>

- <span data-ttu-id="0278d-141">自訂包裝函式</span><span class="sxs-lookup"><span data-stu-id="0278d-141">Custom wrappers</span></span>

  <span data-ttu-id="0278d-142">當型別程式庫無法使用或不正確時，其中一項選擇就是在 Managed 原始程式碼中建立類別或介面的重複定義。</span><span class="sxs-lookup"><span data-stu-id="0278d-142">When a type library is unavailable or incorrect, one option is to create a duplicate definition of the class or interface in managed source code.</span></span> <span data-ttu-id="0278d-143">然後，您可以使用以執行階段為目標的編譯器編譯這個原始程式碼，以產生組件中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0278d-143">You then compile the source code with a compiler that targets the runtime to produce metadata in an assembly.</span></span>

  <span data-ttu-id="0278d-144">若要以手動方式定義 COM 類型，您必須擁有下列項目的存取權：</span><span class="sxs-lookup"><span data-stu-id="0278d-144">To define COM types manually, you must have access to the following items:</span></span>

  - <span data-ttu-id="0278d-145">要定義的 coclass 和介面的精確描述。</span><span class="sxs-lookup"><span data-stu-id="0278d-145">Precise descriptions of the coclasses and interfaces being defined.</span></span>

  - <span data-ttu-id="0278d-146">可產生適當 .NET Framework 類別定義的編譯器，例如 C# 編譯器。</span><span class="sxs-lookup"><span data-stu-id="0278d-146">A compiler, such as the C# compiler, that can generate the appropriate .NET Framework class definitions.</span></span>

  - <span data-ttu-id="0278d-147">型別程式庫轉換為組件的轉換規則知識。</span><span class="sxs-lookup"><span data-stu-id="0278d-147">Knowledge of the type library-to-assembly conversion rules.</span></span>

  <span data-ttu-id="0278d-148">撰寫自訂包裝函式是進階技術。</span><span class="sxs-lookup"><span data-stu-id="0278d-148">Writing a custom wrapper is an advanced technique.</span></span> <span data-ttu-id="0278d-149">如需如何產生自訂包裝函式的詳細資訊，請參閱[自訂標準包裝函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="0278d-149">For additional information about how to generate a custom wrapper, see [Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100)).</span></span>

 <span data-ttu-id="0278d-150">如需 COM Interop 匯入處理序的詳細資訊，請參閱[型別程式庫至組件轉換的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="0278d-150">For more information about the COM interop import process, see [Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="0278d-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0278d-151">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- [<span data-ttu-id="0278d-152">將 COM 元件公開給 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0278d-152">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- <span data-ttu-id="0278d-153">[型別程式庫至組件轉換的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0278d-153">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>
- [<span data-ttu-id="0278d-154">Tlbimp.exe （類型程式庫匯入工具）</span><span class="sxs-lookup"><span data-stu-id="0278d-154">Tlbimp.exe (Type Library Importer)</span></span>](../tools/tlbimp-exe-type-library-importer.md)
- <span data-ttu-id="0278d-155">[自訂標準包裝函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0278d-155">[Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="0278d-156">[在受控程式碼中使用 COM 型別](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0278d-156">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="0278d-157">編譯 Interop 專案</span><span class="sxs-lookup"><span data-stu-id="0278d-157">Compiling an Interop Project</span></span>](compiling-an-interop-project.md)
- [<span data-ttu-id="0278d-158">部署 Interop 應用程式</span><span class="sxs-lookup"><span data-stu-id="0278d-158">Deploying an Interop Application</span></span>](deploying-an-interop-application.md)
- [<span data-ttu-id="0278d-159">作法：將參考新增至型別程式庫</span><span class="sxs-lookup"><span data-stu-id="0278d-159">How to: Add References to Type Libraries</span></span>](how-to-add-references-to-type-libraries.md)
- [<span data-ttu-id="0278d-160">作法：從型別程式庫產生 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="0278d-160">How to: Generate Interop Assemblies from Type Libraries</span></span>](how-to-generate-interop-assemblies-from-type-libraries.md)
