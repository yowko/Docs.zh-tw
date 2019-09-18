---
title: 反映和 .NET Native
ms.date: 03/30/2017
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17b567fe0f476e689a9775c5c73ebf068424e840
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049279"
---
# <a name="reflection-and-net-native"></a><span data-ttu-id="a495e-102">反映和 .NET Native</span><span class="sxs-lookup"><span data-stu-id="a495e-102">Reflection and .NET Native</span></span>
<span data-ttu-id="a495e-103">在 .NET Framework 中，Managed 開發可透過反映 API 來支援 metaprogramming。</span><span class="sxs-lookup"><span data-stu-id="a495e-103">In the .NET Framework, managed development supports metaprogramming through the reflection API.</span></span> <span data-ttu-id="a495e-104">反映可讓您檢查應用程式中的物件、在透過檢查發現的物件上呼叫方法、在執行階段產生新的類型，並可支援許多其他動態程式碼案例。</span><span class="sxs-lookup"><span data-stu-id="a495e-104">Reflection allows you to inspect objects in an app, call methods on objects discovered through inspection, generate new types at run time, and supports many other dynamic code scenarios.</span></span> <span data-ttu-id="a495e-105">它也支援序列化和還原序列化，可讓物件的欄位值保存下來，並於稍後還原。</span><span class="sxs-lookup"><span data-stu-id="a495e-105">It also supports serialization and deserialization, which allows an object's field values to be persisted and later restored.</span></span> <span data-ttu-id="a495e-106">這些案例全都需要 .NET Framework just-in-time (JIT) 編譯器依據可用的中繼資料來產生機器碼。</span><span class="sxs-lookup"><span data-stu-id="a495e-106">These scenarios all require the .NET Framework just-in-time (JIT) compiler to generate native code based on available metadata.</span></span>  
  
 <span data-ttu-id="a495e-107">.NET Native 執行時間不包含 JIT 編譯程式。</span><span class="sxs-lookup"><span data-stu-id="a495e-107">The .NET Native runtime doesn't include a JIT compiler.</span></span> <span data-ttu-id="a495e-108">因此，必須事先產生所有必要的機器碼。</span><span class="sxs-lookup"><span data-stu-id="a495e-108">As a result, all necessary native code must be generated in advance.</span></span> <span data-ttu-id="a495e-109">系統會使用一組啟發學習法來判斷應該產生哪些程式碼，但這些啟發學習法無法涵蓋所有可能的 metaprogramming 案例。</span><span class="sxs-lookup"><span data-stu-id="a495e-109">A set of heuristics is used to determine what code should be generated, but these heuristics cannot cover all possible metaprogramming scenarios.</span></span>  <span data-ttu-id="a495e-110">因此，您必須使用[執行階段指示詞](runtime-directives-rd-xml-configuration-file-reference.md)，提供提示給這些 metaprogramming 案例。</span><span class="sxs-lookup"><span data-stu-id="a495e-110">Therefore, you must provide hints for these metaprogramming scenarios by using [runtime directives](runtime-directives-rd-xml-configuration-file-reference.md).</span></span> <span data-ttu-id="a495e-111">如果在執行階段時未提供必要的中繼資料或實作程式碼，則應用程式會擲回 [MissingMetadataException](missingmetadataexception-class-net-native.md)、[MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 或 [MissingInteropDataException](missinginteropdataexception-class-net-native.md) 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a495e-111">If the necessary metadata or implementation code is not available at runtime, your app throws a [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md), or [MissingInteropDataException](missinginteropdataexception-class-net-native.md) exception.</span></span> <span data-ttu-id="a495e-112">您可以使用兩個疑難排解工具，這些工具會產生可讓執行階段指示詞檔案消除例外狀況的適當項目：</span><span class="sxs-lookup"><span data-stu-id="a495e-112">Two troubleshooters are available that will generate the appropriate entry for your runtime directives file that eliminates the exception:</span></span>  
  
- <span data-ttu-id="a495e-113">針對類型的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/type.html) 。</span><span class="sxs-lookup"><span data-stu-id="a495e-113">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/type.html) for types.</span></span>  
  
- <span data-ttu-id="a495e-114">針對方法的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/method.html) 。</span><span class="sxs-lookup"><span data-stu-id="a495e-114">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/method.html) for methods.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a495e-115">如需 .NET 原生編譯程序的概觀 (其提供需要執行階段指示詞檔案的背景資訊)，請參閱 [.NET 原生和編譯](net-native-and-compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="a495e-115">For an overview of the .NET Native compilation process that provides background on why a runtime directives file is needed, see [.NET Native and Compilation](net-native-and-compilation.md).</span></span>  
  
 <span data-ttu-id="a495e-116">此外，.NET Native 不允許您反映 .NET Framework Class Library 的私用成員。</span><span class="sxs-lookup"><span data-stu-id="a495e-116">In addition, .NET Native doesn't allow you to reflect over private members of the .NET Framework class library.</span></span> <span data-ttu-id="a495e-117">例如，呼叫 <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> 屬性來擷取 .NET Framework 類別庫類型，只會傳回公用或受保護的欄位。</span><span class="sxs-lookup"><span data-stu-id="a495e-117">For example, a call to the <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> property to retrieve the fields of a .NET Framework class library type returns only public or protected fields.</span></span>  
  
 <span data-ttu-id="a495e-118">下列主題提供您在應用程式中支援反映和序列化時，所需的概念和參考文件：</span><span class="sxs-lookup"><span data-stu-id="a495e-118">The following topics provide the conceptual and reference documentation that you need to support reflection and serialization in your apps:</span></span>  
  
- [<span data-ttu-id="a495e-119">依賴反映的 API</span><span class="sxs-lookup"><span data-stu-id="a495e-119">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)  
  
- [<span data-ttu-id="a495e-120">反映 API 參考</span><span class="sxs-lookup"><span data-stu-id="a495e-120">Reflection API Reference</span></span>](net-native-reflection-api-reference.md)  
  
- [<span data-ttu-id="a495e-121">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="a495e-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="a495e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a495e-122">See also</span></span>

- [<span data-ttu-id="a495e-123">使用 .NET Native 編譯應用程式</span><span class="sxs-lookup"><span data-stu-id="a495e-123">Compiling Apps with .NET Native</span></span>](index.md)
- [<span data-ttu-id="a495e-124">.NET Native 和編譯</span><span class="sxs-lookup"><span data-stu-id="a495e-124">.NET Native and Compilation</span></span>](net-native-and-compilation.md)
