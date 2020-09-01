---
description: '-可為 null (c # 編譯器選項) '
title: '-可為 null (c # 編譯器選項) '
author: IEvangelist
ms.author: dapine
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: f9c6c204d2563865f741c6ddb4644eb56f956c12
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125042"
---
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="dccfb-103">-可為 null (c # 編譯器選項) </span><span class="sxs-lookup"><span data-stu-id="dccfb-103">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="dccfb-104">**-可為 null**的選項可讓您指定所需的可為 null 內容。</span><span class="sxs-lookup"><span data-stu-id="dccfb-104">The **-nullable** option lets you specify the desired nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="dccfb-105">語法</span><span class="sxs-lookup"><span data-stu-id="dccfb-105">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="dccfb-106">引數</span><span class="sxs-lookup"><span data-stu-id="dccfb-106">Arguments</span></span>

<span data-ttu-id="dccfb-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="dccfb-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="dccfb-108">指定 `+` （或只是 **可為 null**）會導致編譯器啟用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="dccfb-108">Specifying `+`, or just **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="dccfb-109">指定 `-` ，如果您未指定 **-可為 null**，則會停用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="dccfb-109">Specifying `-`, which is in effect if you do not specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="dccfb-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span><span class="sxs-lookup"><span data-stu-id="dccfb-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="dccfb-111">指定可為 null 的內容選項。</span><span class="sxs-lookup"><span data-stu-id="dccfb-111">Specifies the nullable context option.</span></span> <span data-ttu-id="dccfb-112">類似于 `+` 或 `-` ，表示要啟用和停用，但允許更多的可為 null 內容的精確程度。</span><span class="sxs-lookup"><span data-stu-id="dccfb-112">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="dccfb-113">`enable`引數的作用與您指定 **-nullable**的相同，可啟用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="dccfb-113">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="dccfb-114">指定 `disable` 將會停用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="dccfb-114">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="dccfb-115">提供 `warnings` 引數（ **可為 null：警告**）時，會啟用可為 null 的警告內容。</span><span class="sxs-lookup"><span data-stu-id="dccfb-115">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="dccfb-116">當指定 `annotations` 引數（ **-nullable：注釋**）時，可為 null 注釋內容已啟用。</span><span class="sxs-lookup"><span data-stu-id="dccfb-116">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="dccfb-117">備註</span><span class="sxs-lookup"><span data-stu-id="dccfb-117">Remarks</span></span>

<span data-ttu-id="dccfb-118">流程分析用來推斷可執行程式碼內變數的可 null 性。</span><span class="sxs-lookup"><span data-stu-id="dccfb-118">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="dccfb-119">變數的推斷 null 屬性與變數宣告的可 null 性無關。</span><span class="sxs-lookup"><span data-stu-id="dccfb-119">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="dccfb-120">即使有條件地省略方法呼叫，也會進行分析。</span><span class="sxs-lookup"><span data-stu-id="dccfb-120">Method calls are analyzed even when they are conditionally omitted.</span></span> <span data-ttu-id="dccfb-121">例如， <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 在發行模式中。</span><span class="sxs-lookup"><span data-stu-id="dccfb-121">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="dccfb-122">以下列屬性標注之方法的調用也會影響流程分析：</span><span class="sxs-lookup"><span data-stu-id="dccfb-122">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="dccfb-123">簡單的前置條件： <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="dccfb-123">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="dccfb-124">簡單的後置條件： <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="dccfb-124">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="dccfb-125">條件式後置條件： <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="dccfb-125">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="dccfb-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> 例如， (`DoesNotReturnIf(false)` <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) 和 <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="dccfb-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (for example, `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="dccfb-127">成員後置條件： <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> 和 <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="dccfb-127">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="dccfb-128">若要在專案中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="dccfb-128">To set this compiler option in a project</span></span>

<span data-ttu-id="dccfb-129">編輯 *.csproj* 檔案，以在階層 `<Nullable>` 中新增標記 `Project/PropertyGroup` ：</span><span class="sxs-lookup"><span data-stu-id="dccfb-129">Edit the *.csproj* file to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="dccfb-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dccfb-130">See also</span></span>

- [<span data-ttu-id="dccfb-131">C # 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="dccfb-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="dccfb-132">可為 Null 的參考型別</span><span class="sxs-lookup"><span data-stu-id="dccfb-132">Nullable reference types</span></span>](../../nullable-references.md)
