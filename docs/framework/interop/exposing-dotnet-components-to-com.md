---
title: 將 .NET 元件公開給 COM
description: 將 .NET 元件公開至 COM。 限定交互操作的 .NET 類型。 套用 interop 屬性。 封裝 COM 的元件。 使用 COM 的 managed 類型。
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
ms.openlocfilehash: dc808f3e8d6bd89ba979d43e5b4ec9d787bd09b1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545255"
---
# <a name="exposing-net-components-to-com"></a><span data-ttu-id="8b05d-107">將 .NET 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="8b05d-107">Exposing .NET components to COM</span></span>

<span data-ttu-id="8b05d-108">撰寫 .NET 類型和從 Unmanaged 程式碼取用該類型，對開發人員來說是不同的活動。</span><span class="sxs-lookup"><span data-stu-id="8b05d-108">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="8b05d-109">本節描述幾個撰寫與 COM 用戶端交互操作之 Managed 程式碼的祕訣：</span><span class="sxs-lookup"><span data-stu-id="8b05d-109">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>

- <span data-ttu-id="8b05d-110">[限定交互操作的 .net 類型](../../standard/native-interop/qualify-net-types-for-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="8b05d-110">[Qualifying .NET types for interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

     <span data-ttu-id="8b05d-111">所有您想要公開給 COM 的 Managed 類型、方法、屬性、欄位和事件，都必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="8b05d-111">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="8b05d-112">型別必須有公用無參數建構函式，它是可透過 COM 叫用的唯一建構函式。</span><span class="sxs-lookup"><span data-stu-id="8b05d-112">Types must have a public parameterless constructor, which is the only constructor that can be invoked through COM.</span></span>

- <span data-ttu-id="8b05d-113">套用[interop 屬性](../../standard/native-interop/apply-interop-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="8b05d-113">[Applying interop attributes](../../standard/native-interop/apply-interop-attributes.md).</span></span>

     <span data-ttu-id="8b05d-114">Managed 程式碼中的自訂屬性，可以加強元件的互通性。</span><span class="sxs-lookup"><span data-stu-id="8b05d-114">Custom attributes within managed code can enhance the interoperability of a component.</span></span>

- <span data-ttu-id="8b05d-115">[封裝 COM 的元件](packaging-an-assembly-for-com.md)。</span><span class="sxs-lookup"><span data-stu-id="8b05d-115">[Packaging an assembly for COM](packaging-an-assembly-for-com.md).</span></span>

     <span data-ttu-id="8b05d-116">COM 開發人員可能會要求您彙總參考及部署組件的相關步驟。</span><span class="sxs-lookup"><span data-stu-id="8b05d-116">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>

 <span data-ttu-id="8b05d-117">此外，本節還會找出與從 COM 用戶端取用 Managed 類型的相關工作。</span><span class="sxs-lookup"><span data-stu-id="8b05d-117">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>

## <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="8b05d-118">從 COM 取用 Managed 類型</span><span class="sxs-lookup"><span data-stu-id="8b05d-118">To consume a managed type from COM</span></span>

1. <span data-ttu-id="8b05d-119">[向 COM 登錄組件](registering-assemblies-with-com.md)。</span><span class="sxs-lookup"><span data-stu-id="8b05d-119">[Register assemblies with COM](registering-assemblies-with-com.md).</span></span>

     <span data-ttu-id="8b05d-120">組件 (與型別程式庫) 中的類型必須在設計階段登錄。</span><span class="sxs-lookup"><span data-stu-id="8b05d-120">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="8b05d-121">如果安裝程式不登錄組件，請指示 COM 開發人員使用 Regasm.exe。</span><span class="sxs-lookup"><span data-stu-id="8b05d-121">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>

2. <span data-ttu-id="8b05d-122">[參考 COM 的 .net 類型](how-to-reference-net-types-from-com.md)。</span><span class="sxs-lookup"><span data-stu-id="8b05d-122">[Reference .NET types from COM](how-to-reference-net-types-from-com.md).</span></span>

     <span data-ttu-id="8b05d-123">COM 開發人員可以使用目前所用的相同工具和技術，參考組件中的類型。</span><span class="sxs-lookup"><span data-stu-id="8b05d-123">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>

3. <span data-ttu-id="8b05d-124">[呼叫 .NET 物件](/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="8b05d-124">[Call a .NET object](/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span></span>

     <span data-ttu-id="8b05d-125">COM 開發人員可以用在任何 Unmanaged 類型上呼叫方法的相同方式，在 .NET 物件上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="8b05d-125">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="8b05d-126">例如，COM **CoCreateInstance** API 會啟動 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="8b05d-126">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>

4. <span data-ttu-id="8b05d-127">[部署供 COM 存取的應用程式](/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="8b05d-127">[Deploy an application for COM access](/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span></span>

     <span data-ttu-id="8b05d-128">強式名稱組件可以安裝在全域組件快取，而且需要其發行者的簽章。</span><span class="sxs-lookup"><span data-stu-id="8b05d-128">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="8b05d-129">沒有強式名稱的組件必須安裝在用戶端的應用程式目錄中。</span><span class="sxs-lookup"><span data-stu-id="8b05d-129">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b05d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b05d-130">See also</span></span>

- [<span data-ttu-id="8b05d-131">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="8b05d-131">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="8b05d-132">COM Interop 範例：COM 用戶端與 .NET 伺服器</span><span class="sxs-lookup"><span data-stu-id="8b05d-132">COM Interop Sample: COM Client and .NET Server</span></span>](com-interop-sample-com-client-and-net-server.md)
