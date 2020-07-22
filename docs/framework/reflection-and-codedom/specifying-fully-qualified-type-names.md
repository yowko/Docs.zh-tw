---
title: 指定完整的類型名稱
description: 如需反映作業的有效輸入，請使用完整的類型名稱，其具有元件名稱規格、命名空間規格和類型名稱。
ms.date: 02/21/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- languages, grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
ms.openlocfilehash: ff33b6abd31a82c6b80aa794564c5c48648cde63
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865225"
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="89c5a-103">指定完整的類型名稱</span><span class="sxs-lookup"><span data-stu-id="89c5a-103">Specifying fully qualified type names</span></span>

<span data-ttu-id="89c5a-104">您必須指定具有各種反映作業有效輸入的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="89c5a-104">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="89c5a-105">完整的類型名稱包括組件名稱規格、命名空間規格和類型名稱。</span><span class="sxs-lookup"><span data-stu-id="89c5a-105">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="89c5a-106">方法使用的類型名稱規格如 <xref:System.Type.GetType%2A?displayProperty=nameWithType>、<xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>、<xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> 和 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="89c5a-106">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>

## <a name="grammar-for-type-names"></a><span data-ttu-id="89c5a-107">類型名稱的文法</span><span class="sxs-lookup"><span data-stu-id="89c5a-107">Grammar for type names</span></span>

 <span data-ttu-id="89c5a-108">文法會定義正式語言的語法。</span><span class="sxs-lookup"><span data-stu-id="89c5a-108">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="89c5a-109">下表列出語彙規則，說明如何辨識有效的輸入。</span><span class="sxs-lookup"><span data-stu-id="89c5a-109">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="89c5a-110">終端項 (不會進一步縮減的那些項目) 全部以大寫字母顯示。</span><span class="sxs-lookup"><span data-stu-id="89c5a-110">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="89c5a-111">非終端項 (會進一步縮減的那些項目) 會以大小寫混合或單引號括住的字串顯示，但單引號 (') 不是語法本身的一部分。</span><span class="sxs-lookup"><span data-stu-id="89c5a-111">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="89c5a-112">縱線字元 (&#124;) 表示具有子規則的規則。</span><span class="sxs-lookup"><span data-stu-id="89c5a-112">The pipe character (&#124;) denotes rules that have subrules.</span></span>

<!-- markdownlint-disable MD010 -->
```antlr
TypeSpec
    : ReferenceTypeSpec
    | SimpleTypeSpec
    ;

ReferenceTypeSpec
    : SimpleTypeSpec '&'
    ;

SimpleTypeSpec
    : PointerTypeSpec
    | GenericTypeSpec
    | TypeName
    ;

GenericTypeSpec
   : SimpleTypeSpec ` NUMBER

PointerTypeSpec
    : SimpleTypeSpec '*'
    ;

ArrayTypeSpec
    : SimpleTypeSpec '[ReflectionDimension]'
    | SimpleTypeSpec '[ReflectionEmitDimension]'
    ;

ReflectionDimension
    : '*'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

ReflectionEmitDimension
    : '*'
    | Number '..' Number
    | Number '…'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

Number
    : [0-9]+
    ;

TypeName
    : NamespaceTypeName
    | NamespaceTypeName ',' AssemblyNameSpec
    ;

NamespaceTypeName
    : NestedTypeName
    | NamespaceSpec '.' NestedTypeName
    ;

NestedTypeName
    : IDENTIFIER
    | NestedTypeName '+' IDENTIFIER
    ;

NamespaceSpec
    : IDENTIFIER
    | NamespaceSpec '.' IDENTIFIER
    ;

AssemblyNameSpec
    : IDENTIFIER
    | IDENTIFIER ',' AssemblyProperties
    ;

AssemblyProperties
    : AssemblyProperty
    | AssemblyProperties ',' AssemblyProperty
    ;

AssemblyProperty
    : AssemblyPropertyName '=' AssemblyPropertyValue
    ;
```
<!-- markdownlint-enable MD010 -->

## <a name="specifying-special-characters"></a><span data-ttu-id="89c5a-113">指定特殊字元</span><span class="sxs-lookup"><span data-stu-id="89c5a-113">Specifying special characters</span></span>

<span data-ttu-id="89c5a-114">類型名稱中的 IDENTIFIER 是語言規則判定的任何有效名稱。</span><span class="sxs-lookup"><span data-stu-id="89c5a-114">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>

<span data-ttu-id="89c5a-115">將反斜線 (\\) 用作逸出字元，分隔下列作為 IDENTIFIER 一部分的權杖。</span><span class="sxs-lookup"><span data-stu-id="89c5a-115">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>

|<span data-ttu-id="89c5a-116">Token</span><span class="sxs-lookup"><span data-stu-id="89c5a-116">Token</span></span>|<span data-ttu-id="89c5a-117">意義</span><span class="sxs-lookup"><span data-stu-id="89c5a-117">Meaning</span></span>|
|-----------|-------------|
|<span data-ttu-id="89c5a-118">\\,</span><span class="sxs-lookup"><span data-stu-id="89c5a-118">\\,</span></span>|<span data-ttu-id="89c5a-119">組件分隔符號。</span><span class="sxs-lookup"><span data-stu-id="89c5a-119">Assembly separator.</span></span>|
|\\+|<span data-ttu-id="89c5a-120">巢狀型別分隔符號。</span><span class="sxs-lookup"><span data-stu-id="89c5a-120">Nested type separator.</span></span>|
|\\&|<span data-ttu-id="89c5a-121">參考型別。</span><span class="sxs-lookup"><span data-stu-id="89c5a-121">Reference type.</span></span>|
|\\*|<span data-ttu-id="89c5a-122">指標類型。</span><span class="sxs-lookup"><span data-stu-id="89c5a-122">Pointer type.</span></span>|
|<span data-ttu-id="89c5a-123">\\[</span><span class="sxs-lookup"><span data-stu-id="89c5a-123">\\[</span></span>|<span data-ttu-id="89c5a-124">陣列維度分隔符號。</span><span class="sxs-lookup"><span data-stu-id="89c5a-124">Array dimension delimiter.</span></span>|
|<span data-ttu-id="89c5a-125">\\]</span><span class="sxs-lookup"><span data-stu-id="89c5a-125">\\]</span></span>|<span data-ttu-id="89c5a-126">陣列維度分隔符號。</span><span class="sxs-lookup"><span data-stu-id="89c5a-126">Array dimension delimiter.</span></span>|
|<span data-ttu-id="89c5a-127">\\.</span><span class="sxs-lookup"><span data-stu-id="89c5a-127">\\.</span></span>|<span data-ttu-id="89c5a-128">句號只有用在陣列規格中時，前面才會使用反斜線。</span><span class="sxs-lookup"><span data-stu-id="89c5a-128">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="89c5a-129">NamespaceSpec 中的句號不接受反斜線。</span><span class="sxs-lookup"><span data-stu-id="89c5a-129">Periods in NamespaceSpec do not take the backslash.</span></span>|
|<span data-ttu-id="89c5a-130">\\\|反斜線會視需要當成字串常值。</span><span class="sxs-lookup"><span data-stu-id="89c5a-130">\\\|Backslash when needed as a string literal.</span></span>|

<span data-ttu-id="89c5a-131">請注意，除 AssemblyNameSpec 以外的所有 TypeSpec 元件中，空格都是相關的。</span><span class="sxs-lookup"><span data-stu-id="89c5a-131">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="89c5a-132">在 AssemblyNameSpec 中，',' 分隔符號之前的空格是相關的，但 ',' 分隔符號之後的空格則會忽略。</span><span class="sxs-lookup"><span data-stu-id="89c5a-132">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>

<span data-ttu-id="89c5a-133"><xref:System.Type.FullName%2A?displayProperty=nameWithType> 之類的反映類別會傳回損害的名稱，所以傳回的名稱可用於呼叫 <xref:System.Type.GetType%2A>，如在 `MyType.GetType(myType.FullName)` 中一樣。</span><span class="sxs-lookup"><span data-stu-id="89c5a-133">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>

<span data-ttu-id="89c5a-134">例如，類型的完整名稱可能是 `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`。</span><span class="sxs-lookup"><span data-stu-id="89c5a-134">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>

<span data-ttu-id="89c5a-135">如果以前的命名空間是 `Ozzy.Out+Back`，則反斜線前面必須有加號。</span><span class="sxs-lookup"><span data-stu-id="89c5a-135">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="89c5a-136">否則，剖析器會將它解譯為巢狀分隔符號。</span><span class="sxs-lookup"><span data-stu-id="89c5a-136">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="89c5a-137">反映將此字串發出為 `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`。</span><span class="sxs-lookup"><span data-stu-id="89c5a-137">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>

## <a name="specifying-assembly-names"></a><span data-ttu-id="89c5a-138">指定組件名稱</span><span class="sxs-lookup"><span data-stu-id="89c5a-138">Specifying assembly names</span></span>

<span data-ttu-id="89c5a-139">組件名稱規格中的基本資訊是組件的文字名稱 (IDENTIFIER)。</span><span class="sxs-lookup"><span data-stu-id="89c5a-139">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="89c5a-140">您可以按照逗號分隔的屬性/值組清單理解 IDENTIFIER，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="89c5a-140">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="89c5a-141">IDENTIFIER 的命名應依照檔案命名的規則。</span><span class="sxs-lookup"><span data-stu-id="89c5a-141">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="89c5a-142">IDENTIFIER 不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="89c5a-142">The IDENTIFIER is case-insensitive.</span></span>

|<span data-ttu-id="89c5a-143">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="89c5a-143">Property name</span></span>|<span data-ttu-id="89c5a-144">描述</span><span class="sxs-lookup"><span data-stu-id="89c5a-144">Description</span></span>|<span data-ttu-id="89c5a-145">允許的值</span><span class="sxs-lookup"><span data-stu-id="89c5a-145">Allowable values</span></span>|
|-------------------|-----------------|----------------------|
|<span data-ttu-id="89c5a-146">**版本**</span><span class="sxs-lookup"><span data-stu-id="89c5a-146">**Version**</span></span>|<span data-ttu-id="89c5a-147">組件版本號碼</span><span class="sxs-lookup"><span data-stu-id="89c5a-147">Assembly version number</span></span>|<span data-ttu-id="89c5a-148">在 *Major.Minor.Build.Revision* 中，*Major*、*Minor*、*Build* 和 *Revision* 是介於 0 到 65535 (含) 之間的整數。</span><span class="sxs-lookup"><span data-stu-id="89c5a-148">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|
|<span data-ttu-id="89c5a-149">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="89c5a-149">**PublicKey**</span></span>|<span data-ttu-id="89c5a-150">完整公開金鑰</span><span class="sxs-lookup"><span data-stu-id="89c5a-150">Full public key</span></span>|<span data-ttu-id="89c5a-151">十六進位格式的完整公開金鑰字串值。</span><span class="sxs-lookup"><span data-stu-id="89c5a-151">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="89c5a-152">指定 null 參考 (Visual Basic 為 **Nothing**) 以明確指出私用組件。</span><span class="sxs-lookup"><span data-stu-id="89c5a-152">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="89c5a-153">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="89c5a-153">**PublicKeyToken**</span></span>|<span data-ttu-id="89c5a-154">公開金鑰語彙基元 (完整公開金鑰的 8 位元組雜湊)</span><span class="sxs-lookup"><span data-stu-id="89c5a-154">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="89c5a-155">十六進位格式的公開金鑰語彙基元字串值。</span><span class="sxs-lookup"><span data-stu-id="89c5a-155">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="89c5a-156">指定 null 參考 (Visual Basic 為 **Nothing**) 以明確指出私用組件。</span><span class="sxs-lookup"><span data-stu-id="89c5a-156">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="89c5a-157">**文化特性**</span><span class="sxs-lookup"><span data-stu-id="89c5a-157">**Culture**</span></span>|<span data-ttu-id="89c5a-158">組件文化特性</span><span class="sxs-lookup"><span data-stu-id="89c5a-158">Assembly culture</span></span>|<span data-ttu-id="89c5a-159">RFC-1766 格式的組件文化特性，或「中性的」語言無關 (非附屬) 組件。</span><span class="sxs-lookup"><span data-stu-id="89c5a-159">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|
|<span data-ttu-id="89c5a-160">**Custom**</span><span class="sxs-lookup"><span data-stu-id="89c5a-160">**Custom**</span></span>|<span data-ttu-id="89c5a-161">自訂二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="89c5a-161">Custom binary large object (BLOB).</span></span> <span data-ttu-id="89c5a-162">目前只用於[原生映像產生器 (Ngen)](../tools/ngen-exe-native-image-generator.md) 產生的組件。</span><span class="sxs-lookup"><span data-stu-id="89c5a-162">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="89c5a-163">自訂原生映像產生器工具所用的字串用於通知組件快取安裝中的組件是原生映像，因此要安裝在原生映像快取中。</span><span class="sxs-lookup"><span data-stu-id="89c5a-163">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="89c5a-164">也稱為 zap 字串。</span><span class="sxs-lookup"><span data-stu-id="89c5a-164">Also called a zap string.</span></span>|

<span data-ttu-id="89c5a-165">下例示範的 **AssemblyName**，僅以預設文化特性命名組件。</span><span class="sxs-lookup"><span data-stu-id="89c5a-165">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>

```csharp
com.microsoft.crypto, Culture=""
```

<span data-ttu-id="89c5a-166">下例顯示具有 "en" 文化特性之強式名稱組件的完整指定參考。</span><span class="sxs-lookup"><span data-stu-id="89c5a-166">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

<span data-ttu-id="89c5a-167">下列範例各自都有部分指定的 **AssemblyName**，無論強式或簡單名稱組件皆可滿足。</span><span class="sxs-lookup"><span data-stu-id="89c5a-167">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

<span data-ttu-id="89c5a-168">下列範例各自都有部分指定的 **AssemblyName**，必須由簡單名稱組件滿足。</span><span class="sxs-lookup"><span data-stu-id="89c5a-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

<span data-ttu-id="89c5a-169">下列範例各自都有部分指定的 **AssemblyName**，必須由強式名稱組件滿足。</span><span class="sxs-lookup"><span data-stu-id="89c5a-169">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a><span data-ttu-id="89c5a-170">指定泛型型別</span><span class="sxs-lookup"><span data-stu-id="89c5a-170">Specifying generic types</span></span>

<span data-ttu-id="89c5a-171">SimpleTypeSpec\`NUMBER 代表含有 1 到 *n* 泛型型別參數的開放式泛型型別。</span><span class="sxs-lookup"><span data-stu-id="89c5a-171">SimpleTypeSpec\`NUMBER represents an open generic type with from 1 to *n* generic type parameters.</span></span> <span data-ttu-id="89c5a-172">例如，若要取得開放式泛型型別清單 \<T> 或封閉式泛型型別清單的參考，請 \<String> 使用 ``Type.GetType("System.Collections.Generic.List`1")`` 來取得泛型型別字典的參考 \<TKey,TValue> ，請使用 ``Type.GetType("System.Collections.Generic.Dictionary`2")`` 。</span><span class="sxs-lookup"><span data-stu-id="89c5a-172">For example, to get reference to the open generic type List\<T> or the closed generic type List\<String>, use ``Type.GetType("System.Collections.Generic.List`1")`` To get a reference to the generic type Dictionary\<TKey,TValue>, use ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span></span>

## <a name="specifying-pointers"></a><span data-ttu-id="89c5a-173">指定指標</span><span class="sxs-lookup"><span data-stu-id="89c5a-173">Specifying pointers</span></span>

<span data-ttu-id="89c5a-174">SimpleTypeSpec\* 表示 Unmanaged 指標。</span><span class="sxs-lookup"><span data-stu-id="89c5a-174">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="89c5a-175">例如，若要取得類型 MyType 的指標，請使用 `Type.GetType("MyType*")`。</span><span class="sxs-lookup"><span data-stu-id="89c5a-175">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="89c5a-176">若要取得類型 MyType 指標的指標，請使用 `Type.GetType("MyType**")`。</span><span class="sxs-lookup"><span data-stu-id="89c5a-176">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>

## <a name="specifying-references"></a><span data-ttu-id="89c5a-177">指定參考</span><span class="sxs-lookup"><span data-stu-id="89c5a-177">Specifying references</span></span>

<span data-ttu-id="89c5a-178">SimpleTypeSpec & 代表 Managed 指標或參考。</span><span class="sxs-lookup"><span data-stu-id="89c5a-178">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="89c5a-179">例如，若要取得類型 MyType 的參考，請使用 `Type.GetType("MyType &")`。</span><span class="sxs-lookup"><span data-stu-id="89c5a-179">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="89c5a-180">請注意，參考與指標不同，僅限一個層級。</span><span class="sxs-lookup"><span data-stu-id="89c5a-180">Note that unlike pointers, references are limited to one level.</span></span>

## <a name="specifying-arrays"></a><span data-ttu-id="89c5a-181">指定陣列</span><span class="sxs-lookup"><span data-stu-id="89c5a-181">Specifying arrays</span></span>

<span data-ttu-id="89c5a-182">在 BNF 文法中，ReflectionEmitDimension 只適用於使用 <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> 擷取的不完整類型定義。</span><span class="sxs-lookup"><span data-stu-id="89c5a-182">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="89c5a-183">不完整的類型定義是使用 <xref:System.Reflection.Emit?displayProperty=nameWithType> 建構卻未呼叫 <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> 的 <xref:System.Reflection.Emit.TypeBuilder> 物件。</span><span class="sxs-lookup"><span data-stu-id="89c5a-183">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="89c5a-184">ReflectionDimension 可以用來擷取任何已完成的類型定義，也就是已載入的類型。</span><span class="sxs-lookup"><span data-stu-id="89c5a-184">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>

<span data-ttu-id="89c5a-185">指定陣列陣序即可存取反映中的陣列：</span><span class="sxs-lookup"><span data-stu-id="89c5a-185">Arrays are accessed in reflection by specifying the rank of the array:</span></span>

- <span data-ttu-id="89c5a-186">`Type.GetType("MyArray[]")` 會取得下限為 0 的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="89c5a-186">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>

- <span data-ttu-id="89c5a-187">`Type.GetType("MyArray[*]")` 會取得下限不明的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="89c5a-187">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>
- <span data-ttu-id="89c5a-188">`Type.GetType("MyArray[][]")` 會取得二維陣列的陣列。</span><span class="sxs-lookup"><span data-stu-id="89c5a-188">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>

- <span data-ttu-id="89c5a-189">`Type.GetType("MyArray[*,*]")` 和 `Type.GetType("MyArray[,]")` 會取得下限不明的矩形二維陣列。</span><span class="sxs-lookup"><span data-stu-id="89c5a-189">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>

<span data-ttu-id="89c5a-190">請注意，就執行階段而言是 `MyArray[] != MyArray[*]`，但對多維陣列而言，兩種標記法是一樣的。</span><span class="sxs-lookup"><span data-stu-id="89c5a-190">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="89c5a-191">亦即 `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` 評估為 **true**。</span><span class="sxs-lookup"><span data-stu-id="89c5a-191">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>

<span data-ttu-id="89c5a-192">針對**ModuleBuilder**， `MyArray[0..5]` 表示大小為6、下限為0的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="89c5a-192">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="89c5a-193">`MyArray[4…]` 表示大小不明、下限 4 的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="89c5a-193">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="89c5a-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89c5a-194">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [<span data-ttu-id="89c5a-195">檢視類型資訊</span><span class="sxs-lookup"><span data-stu-id="89c5a-195">Viewing Type Information</span></span>](viewing-type-information.md)
