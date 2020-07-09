---
title: '-nullable （c # 編譯器選項）'
author: IEvangelist
ms.author: dapine
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: f1aba7e08f472411640d42f51d78ca6f7e5cc900
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100882"
---
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="f5431-102">-nullable （c # 編譯器選項）</span><span class="sxs-lookup"><span data-stu-id="f5431-102">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="f5431-103">**-Nullable**選項可讓您指定所需的可為 null 內容。</span><span class="sxs-lookup"><span data-stu-id="f5431-103">The **-nullable** option lets you specify the desired nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="f5431-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5431-104">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="f5431-105">引數</span><span class="sxs-lookup"><span data-stu-id="f5431-105">Arguments</span></span>

<span data-ttu-id="f5431-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f5431-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="f5431-107">指定 `+` 或**可為 null**，會使編譯器啟用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="f5431-107">Specifying `+`, or just **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="f5431-108">指定 `-` ，如果您未指定 **-nullable**，則會停用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="f5431-108">Specifying `-`, which is in effect if you do not specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="f5431-109">`enable`&#124; `disable` &#124; `warnings` &#124;`annotations`</span><span class="sxs-lookup"><span data-stu-id="f5431-109">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="f5431-110">指定可為 null 的內容選項。</span><span class="sxs-lookup"><span data-stu-id="f5431-110">Specifies the nullable context option.</span></span> <span data-ttu-id="f5431-111">類似于 `+` 或 `-` ，可啟用和停用，但允許更細微的可為 null 內容的精確程度。</span><span class="sxs-lookup"><span data-stu-id="f5431-111">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="f5431-112">`enable`引數的作用與您指定 **-nullable**相同，會啟用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="f5431-112">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="f5431-113">指定 `disable` 將會停用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="f5431-113">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="f5431-114">提供 `warnings` 引數時，**可為 null：警告**，可為 null 警告內容已啟用。</span><span class="sxs-lookup"><span data-stu-id="f5431-114">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="f5431-115">當指定 `annotations` 引數時，**可為 null**的注釋內容已啟用。</span><span class="sxs-lookup"><span data-stu-id="f5431-115">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5431-116">備註</span><span class="sxs-lookup"><span data-stu-id="f5431-116">Remarks</span></span>

<span data-ttu-id="f5431-117">流程分析是用來推斷可執行程式碼中變數的 null 屬性。</span><span class="sxs-lookup"><span data-stu-id="f5431-117">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="f5431-118">變數的推斷 null 屬性與變數的宣告 null 屬性無關。</span><span class="sxs-lookup"><span data-stu-id="f5431-118">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="f5431-119">方法呼叫即使有條件地省略也會進行分析。</span><span class="sxs-lookup"><span data-stu-id="f5431-119">Method calls are analyzed even when they are conditionally omitted.</span></span> <span data-ttu-id="f5431-120">例如， <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 在發行模式中。</span><span class="sxs-lookup"><span data-stu-id="f5431-120">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="f5431-121">以下列屬性標注之方法的調用也會影響流程分析：</span><span class="sxs-lookup"><span data-stu-id="f5431-121">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="f5431-122">簡單的前置條件： <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> 和<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="f5431-122">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="f5431-123">簡單的後置條件： <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> 和<xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="f5431-123">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="f5431-124">條件式後置條件： <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> 和<xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="f5431-124">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="f5431-125"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute>（例如， `DoesNotReturnIf(false)` 針對 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ）和<xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="f5431-125"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (for example, `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="f5431-126">成員後置條件： <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> 和<xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="f5431-126">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="f5431-127">若要在專案中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="f5431-127">To set this compiler option in a project</span></span>

<span data-ttu-id="f5431-128">編輯 *.csproj*檔案，在階層內新增 `<Nullable>` 標記 `Project/PropertyGroup` ：</span><span class="sxs-lookup"><span data-stu-id="f5431-128">Edit the *.csproj* file to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="f5431-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5431-129">See also</span></span>

- [<span data-ttu-id="f5431-130">C # 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="f5431-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f5431-131">可為 Null 的參考型別</span><span class="sxs-lookup"><span data-stu-id="f5431-131">Nullable reference types</span></span>](../../nullable-references.md)
