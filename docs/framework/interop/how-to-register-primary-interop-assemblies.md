---
title: 作法：登錄主要 Interop 組件
ms.date: 03/30/2017
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e599696b75ed1a0186276dfa47baef2cdf9d7097
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629387"
---
# <a name="how-to-register-primary-interop-assemblies"></a><span data-ttu-id="d11d5-102">作法：登錄主要 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="d11d5-102">How to: Register Primary Interop Assemblies</span></span>

<span data-ttu-id="d11d5-103">類別只能由 COM Interop 封送處理，並且一律會封送處理為介面。</span><span class="sxs-lookup"><span data-stu-id="d11d5-103">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="d11d5-104">在某些情況下，用來封送處理類別的介面就是所謂的類別介面。</span><span class="sxs-lookup"><span data-stu-id="d11d5-104">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="d11d5-105">如需以您選擇的介面來覆寫類別介面的資訊，請參閱 [COM 可呼叫包裝函式](../../../docs/standard/native-interop/com-callable-wrapper.md)。</span><span class="sxs-lookup"><span data-stu-id="d11d5-105">For information about overriding the class interface with an interface of your choice, see [COM Callable Wrapper](../../../docs/standard/native-interop/com-callable-wrapper.md).</span></span>

 <span data-ttu-id="d11d5-106">雖然想要從 .NET Framework 應用程式使用 COM 類型的任何開發人員都可以產生 Interop 組件，但這樣做會有問題。</span><span class="sxs-lookup"><span data-stu-id="d11d5-106">Although any developer who wants to use COM types from a .NET Framework application can generate an interop assembly, doing so creates a problem.</span></span> <span data-ttu-id="d11d5-107">每當開發人員匯入及簽署 COM 類型程式庫時，該開發人員會建立一組唯一類型，而這些類型會與另一個開發人員匯入及簽署的類型不相容。</span><span class="sxs-lookup"><span data-stu-id="d11d5-107">Each time a developer imports and signs a COM type library, that developer creates a set of unique types that are incompatible with those imported and signed by another developer.</span></span> <span data-ttu-id="d11d5-108">這個類型不相容問題的解決方法可讓每個開發人員取得廠商提供及簽署的主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="d11d5-108">The solution to this type incompatibility problem is for each developer to obtain the vendor-supplied and signed primary interop assembly.</span></span>

 <span data-ttu-id="d11d5-109">如果您打算向其他應用程式公開協力廠商 COM 類型，請一律使用與其定義之類型程式庫相同的發行者所提供的主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="d11d5-109">If you plan to expose third-party COM types to other applications, always use the primary interop assembly provided by the same publisher as the type library it defines.</span></span> <span data-ttu-id="d11d5-110">除了提供保證的類型相容性，廠商也常常會自訂主要 Interop 組件來增強互通性。</span><span class="sxs-lookup"><span data-stu-id="d11d5-110">In addition to providing guaranteed type compatibility, primary interop assemblies are often customized by the vendor to enhance interoperability.</span></span>

 <span data-ttu-id="d11d5-111">即使您不打算公開協力廠商 COM 類型，使用主要 Interop 組件也可以簡化與 COM 元件的互通工作。</span><span class="sxs-lookup"><span data-stu-id="d11d5-111">Even if you do not plan to expose third-party COM types, using the primary interop assembly can ease the task of interoperating with COM components.</span></span> <span data-ttu-id="d11d5-112">不過，此策略不會針對廠商可能對主要 Interop 組件中定義之類型的變更進行隔離。</span><span class="sxs-lookup"><span data-stu-id="d11d5-112">However, this strategy provides no insulation from changes a vendor might make to types defined in a primary interop assembly.</span></span> <span data-ttu-id="d11d5-113">當您的應用程式需要這類隔離時，請產生您自己的 Interop 組件，而不要使用主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="d11d5-113">When your application requires such insulation, generate your own interop assembly instead of using the primary interop assembly.</span></span>

 <span data-ttu-id="d11d5-114">您必須先在開發電腦上註冊所有取得的主要 Interop 組件，才能使用 Visual Studio 來加以參考。</span><span class="sxs-lookup"><span data-stu-id="d11d5-114">You must register all acquired primary interop assemblies on your development computer before you can reference them with Visual Studio.</span></span> <span data-ttu-id="d11d5-115">Visual Studio 會在您第一次從 COM 類型程式庫參考類型時，尋找並使用主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="d11d5-115">Visual Studio looks for and uses a primary interop assembly the first time that you reference a type from a COM type library.</span></span> <span data-ttu-id="d11d5-116">如果 Visual Studio 找不到與類型程式庫相關聯的主要 Interop 組件，它會提示您取得該組件，或是提供您建立 Interop 組件的方式。</span><span class="sxs-lookup"><span data-stu-id="d11d5-116">If Visual Studio cannot locate the primary interop assembly associated with the type library, it prompts you to acquire it or offers to create an interop assembly instead.</span></span> <span data-ttu-id="d11d5-117">同樣地，[型別程式庫匯入工具 (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) 也會使用登錄來找出主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="d11d5-117">Likewise, the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) also uses the registry to locate primary interop assemblies.</span></span>

 <span data-ttu-id="d11d5-118">雖然除非您打算使用 Visual Studio，否則並不需要註冊主要 Interop 組件，但註冊有兩個優點：</span><span class="sxs-lookup"><span data-stu-id="d11d5-118">Although it is not necessary to register primary interop assemblies unless you plan to use Visual Studio, registration provides two advantages:</span></span>

- <span data-ttu-id="d11d5-119">已註冊的主要 Interop 組件會明確標示在原始類型程式庫的登錄機碼底下。</span><span class="sxs-lookup"><span data-stu-id="d11d5-119">A registered primary interop assembly is clearly marked under the registry key of the original type library.</span></span> <span data-ttu-id="d11d5-120">註冊是您在電腦上尋找主要 Interop 組件的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="d11d5-120">Registration is the best way for you to locate a primary interop assembly on your computer.</span></span>

- <span data-ttu-id="d11d5-121">如果未來某些時候，您會使用 Visual Studio 來參考具有未註冊主要 Interop 組件的類型，就可以避免不小心產生及使用新的 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="d11d5-121">You can avoid accidentally generating and using a new interop assembly if, at some time in the future, you do use Visual Studio to reference a type for which you have an unregistered primary interop assembly.</span></span>

<span data-ttu-id="d11d5-122">使用[組件註冊工具 (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) 來註冊主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="d11d5-122">Use the [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) to register a primary interop assembly.</span></span>

## <a name="to-register-a-primary-interop-assembly"></a><span data-ttu-id="d11d5-123">註冊主要 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="d11d5-123">To register a primary interop assembly</span></span>

1. <span data-ttu-id="d11d5-124">在命令提示中，輸入：</span><span class="sxs-lookup"><span data-stu-id="d11d5-124">At the command prompt, type:</span></span>

     <span data-ttu-id="d11d5-125">**regasm** *assemblyname*</span><span class="sxs-lookup"><span data-stu-id="d11d5-125">**regasm** *assemblyname*</span></span>

     <span data-ttu-id="d11d5-126">在這個命令中，*assemblyname* 是已註冊組件的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d11d5-126">In this command, *assemblyname* is the file name of the assembly that is registered.</span></span> <span data-ttu-id="d11d5-127">Regasm.exe 會在與原始類型程式庫相同的登錄機碼之下，加入主要 Interop 組件的項目。</span><span class="sxs-lookup"><span data-stu-id="d11d5-127">Regasm.exe adds an entry for the primary interop assembly under the same registry key as the original type library.</span></span>

## <a name="example"></a><span data-ttu-id="d11d5-128">範例</span><span class="sxs-lookup"><span data-stu-id="d11d5-128">Example</span></span>
 <span data-ttu-id="d11d5-129">下列範例會註冊 `CompanyA.UtilLib.dll` 主要 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="d11d5-129">The following example registers the `CompanyA.UtilLib.dll` primary interop assembly.</span></span>

```console
regasm CompanyA.UtilLib.dll
```

## <a name="see-also"></a><span data-ttu-id="d11d5-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d11d5-130">See also</span></span>

- <span data-ttu-id="d11d5-131">[使用主要 Interop 組件設計程式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/baxfadst(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d11d5-131">[Programming with Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/baxfadst(v=vs.100))</span></span>
- <span data-ttu-id="d11d5-132">[找出主要 Interop 組件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y06sxw56(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d11d5-132">[Locating Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y06sxw56(v=vs.100))</span></span>
- <span data-ttu-id="d11d5-133">[轉散發主要 Interop 組件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0dt2w20(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d11d5-133">[Redistributing Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0dt2w20(v=vs.100))</span></span>
