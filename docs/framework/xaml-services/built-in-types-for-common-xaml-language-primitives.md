---
title: 通用 XAML 語言基本類型的內建類型
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: f6225dfcc02b90da58ccafd5c70726b6f80f29d4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45595526"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a><span data-ttu-id="594fc-102">通用 XAML 語言基本類型的內建類型</span><span class="sxs-lookup"><span data-stu-id="594fc-102">Built-in Types for Common XAML Language Primitives</span></span>
<span data-ttu-id="594fc-103">XAML 2009 引進數種資料類型的 XAML 語言層級支援，而這些資料類型是 Common Language Runtime (CLR) 和其他程式設計語言中的常用基本類型。</span><span class="sxs-lookup"><span data-stu-id="594fc-103">XAML 2009 introduces XAML language-level support for several data types that are frequently used primitives in the common language runtime (CLR) and in other programming languages.</span></span> <span data-ttu-id="594fc-104">XAML 2009 新增下列基本類型的支援： `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`和 `x:Array`。</span><span class="sxs-lookup"><span data-stu-id="594fc-104">XAML 2009 adds support for these primitives: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, and `x:Array`</span></span>  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a><span data-ttu-id="594fc-105">XAML 標記中語言基本類型的先前技術</span><span class="sxs-lookup"><span data-stu-id="594fc-105">Previous Techniques for Language Primitives in XAML Markup</span></span>  
 <span data-ttu-id="594fc-106">在舊版 WPF 的 XAML 中，對應內含 .NET Framework 之 CLR 基本類型定義類別的組件和命名空間，即可參考 CLR 語言基本類型。</span><span class="sxs-lookup"><span data-stu-id="594fc-106">In XAML for previous WPF versions, you could reference the CLR language primitives by mapping the assembly and namespace that contained a CLR primitive definition class for the .NET Framework.</span></span> <span data-ttu-id="594fc-107">其中大部分是在 mscorlib 組件和 <xref:System> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="594fc-107">Most of these are in the mscorlib assembly and <xref:System> namespace.</span></span> <span data-ttu-id="594fc-108">例如，若要使用 <xref:System.Int32>，您可以宣告下列對應 (具有後面顯示的範例使用方式)：</span><span class="sxs-lookup"><span data-stu-id="594fc-108">For example, to use <xref:System.Int32>, you could declare the following mapping (with an example usage shown thereafter):</span></span>  
  
```  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a><span data-ttu-id="594fc-109">XAML 2009 語言基本類型</span><span class="sxs-lookup"><span data-stu-id="594fc-109">XAML 2009 Language Primitives</span></span>  
 <span data-ttu-id="594fc-110">根據慣例，會顯示 XAML 的語言基本類型和所有其他 XAML 語言項目 (包括 `x:` 前置詞)。</span><span class="sxs-lookup"><span data-stu-id="594fc-110">By convention, the language primitives for XAML and all other XAML language elements are shown, including the `x:` prefix.</span></span> <span data-ttu-id="594fc-111">這是一般如何在實際標記中使用 XAML 語言項目。</span><span class="sxs-lookup"><span data-stu-id="594fc-111">This is how XAML language elements are typically used in real-world markup.</span></span> <span data-ttu-id="594fc-112">WPF 和 XAML 規格中 XAML 概念文件中會遵循這個慣例。</span><span class="sxs-lookup"><span data-stu-id="594fc-112">This convention is followed in the conceptual documentation for XAML in WPF and also in the XAML specification.</span></span>  
  
### <a name="xobject"></a><span data-ttu-id="594fc-113">x:Object</span><span class="sxs-lookup"><span data-stu-id="594fc-113">x:Object</span></span>  
 <span data-ttu-id="594fc-114">對於 CLR 支援， `x:Object` 基本類型對應至 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="594fc-114">For CLR backing, the `x:Object` primitive corresponds to <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="594fc-115">此基本類型通常不會用於應用程式標記中，但在某些情況下可能十分有用，例如檢查 XAML 類型系統中的指派性。</span><span class="sxs-lookup"><span data-stu-id="594fc-115">This primitive is not typically used in application markup, but might be useful for some scenarios such as checking assignability in a XAML type system.</span></span>  
  
### <a name="xboolean"></a><span data-ttu-id="594fc-116">x:Boolean</span><span class="sxs-lookup"><span data-stu-id="594fc-116">x:Boolean</span></span>  
 <span data-ttu-id="594fc-117">對於 CLR 支援， `x:Boolean` 基本類型對應至 <xref:System.Boolean>。</span><span class="sxs-lookup"><span data-stu-id="594fc-117">For CLR backing, the `x:Boolean` primitive corresponds to <xref:System.Boolean>.</span></span>  
  
 <span data-ttu-id="594fc-118">XAML 將 `x:Boolean` 的值剖析為不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="594fc-118">XAML parses values for `x:Boolean` as case insensitive.</span></span> <span data-ttu-id="594fc-119">請注意， `x:Bool` 不是可接受的替代方案。</span><span class="sxs-lookup"><span data-stu-id="594fc-119">Note that `x:Bool` is not an accepted alternative.</span></span> <span data-ttu-id="594fc-120">如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.17 和 5.4.11 節](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="594fc-120">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.17 and 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xchar"></a><span data-ttu-id="594fc-121">x:Char</span><span class="sxs-lookup"><span data-stu-id="594fc-121">x:Char</span></span>  
 <span data-ttu-id="594fc-122">對於 CLR 支援， `x:Char` 基本類型對應至 <xref:System.Char>。</span><span class="sxs-lookup"><span data-stu-id="594fc-122">For CLR backing, the `x:Char` primitive corresponds to <xref:System.Char>.</span></span>  
  
 <span data-ttu-id="594fc-123">字串和 char 類型會與 XML 層級之檔案的整體編碼間互動。</span><span class="sxs-lookup"><span data-stu-id="594fc-123">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="594fc-124">如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.7 和 5.4.1 節](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="594fc-124">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.7 and 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xstring"></a><span data-ttu-id="594fc-125">x:String</span><span class="sxs-lookup"><span data-stu-id="594fc-125">x:String</span></span>  
 <span data-ttu-id="594fc-126">對於 CLR 支援， `x:String` 基本類型對應至 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="594fc-126">For CLR backing, the `x:String` primitive corresponds to <xref:System.String>.</span></span>  
  
 <span data-ttu-id="594fc-127">字串和 char 類型會與 XML 層級之檔案的整體編碼間互動。</span><span class="sxs-lookup"><span data-stu-id="594fc-127">String and char types have interaction with the overall encoding of the file at the XML level.</span></span> <span data-ttu-id="594fc-128">如需 XAML 語言規格定義，請參閱[ \[MS XAML\] 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="594fc-128">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdecimal"></a><span data-ttu-id="594fc-129">x:Decimal</span><span class="sxs-lookup"><span data-stu-id="594fc-129">x:Decimal</span></span>  
 <span data-ttu-id="594fc-130">對於 CLR 支援， `x:Decimal` 基本類型對應至 <xref:System.Decimal>。</span><span class="sxs-lookup"><span data-stu-id="594fc-130">For CLR backing, the `x:Decimal` primitive corresponds to <xref:System.Decimal>.</span></span>  
  
 <span data-ttu-id="594fc-131">請注意，XAML 剖析原本是在 `en-US` 文化特性下執行。</span><span class="sxs-lookup"><span data-stu-id="594fc-131">Note that XAML parsing is inherently done under `en-US` culture.</span></span> <span data-ttu-id="594fc-132">在 `en-US` 文化特性下，小數點之元件的正確分隔符號一律是句號 (`.`)，不論開發環境的文化特性設定為何，或在執行階段載入 XAML 之最終用戶端目標的文化特性設定為何。</span><span class="sxs-lookup"><span data-stu-id="594fc-132">Under `en-US` culture, the correct separator for the components of a decimal is always a period (`.`) regardless of culture settings of the development environment, or of the eventual client target where the XAML is loaded at run time.</span></span>  
  
 <span data-ttu-id="594fc-133">如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.14 和 5.4.8 節](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="594fc-133">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.14 and 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xsingle"></a><span data-ttu-id="594fc-134">x:Single</span><span class="sxs-lookup"><span data-stu-id="594fc-134">x:Single</span></span>  
 <span data-ttu-id="594fc-135">對於 CLR 支援， `x:Single` 基本類型對應至 <xref:System.Single>。</span><span class="sxs-lookup"><span data-stu-id="594fc-135">For CLR backing, the `x:Single` primitive corresponds to <xref:System.Single>.</span></span>  
  
 <span data-ttu-id="594fc-136">除了數值之外，`x:Single` 的文字語法也允許語彙基元 `Infinity``-Infinity` 和 `NaN`。</span><span class="sxs-lookup"><span data-stu-id="594fc-136">In addition to the numeric values, text syntax for `x:Single` also permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="594fc-137">這些語彙基元視為區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="594fc-137">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="594fc-138">如果文字語法中的第一個字元是`x:Single` 或 `e` ， `E`可以支援科學標記法格式的值。</span><span class="sxs-lookup"><span data-stu-id="594fc-138">`x:Single` can support values in scientific notation form, if the first character in text syntax is `e` or `E`.</span></span>  
  
 <span data-ttu-id="594fc-139">如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.8 和 5.4.2 節](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="594fc-139">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.8 and 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xdouble"></a><span data-ttu-id="594fc-140">x:Double</span><span class="sxs-lookup"><span data-stu-id="594fc-140">x:Double</span></span>  
 <span data-ttu-id="594fc-141">對於 CLR 支援， `x:Double` 基本類型對應至 <xref:System.Double>。</span><span class="sxs-lookup"><span data-stu-id="594fc-141">For CLR backing, the `x:Double` primitive corresponds to <xref:System.Double>.</span></span>  
  
 <span data-ttu-id="594fc-142">除了數值之外，`x:Double` 的文字語法還允許語彙基元 `Infinity``-Infinity` 和 `NaN`。</span><span class="sxs-lookup"><span data-stu-id="594fc-142">In addition to the numeric values, text syntax for `x:Double` permits the tokens `Infinity`, `-Infinity`, and `NaN`.</span></span> <span data-ttu-id="594fc-143">這些語彙基元視為區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="594fc-143">These tokens are treated as case sensitive.</span></span>  
  
 <span data-ttu-id="594fc-144">`x:Double` 可以支援科學標記法格式的值。</span><span class="sxs-lookup"><span data-stu-id="594fc-144">`x:Double` can support values in scientific notation form.</span></span> <span data-ttu-id="594fc-145">使用字元 `e` 或 `E` 導入指數部分。</span><span class="sxs-lookup"><span data-stu-id="594fc-145">Use the character `e` or `E` to introduce the exponent portion.</span></span>  
  
 <span data-ttu-id="594fc-146">如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.9 和 5.4.3 節](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="594fc-146">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.9 and 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint16"></a><span data-ttu-id="594fc-147">x:Int16</span><span class="sxs-lookup"><span data-stu-id="594fc-147">x:Int16</span></span>  
 <span data-ttu-id="594fc-148">對於 CLR 支援， `x:Int16` 基本類型對應至 <xref:System.Int16> ，並將 `x:Int16` 視為帶正負號。</span><span class="sxs-lookup"><span data-stu-id="594fc-148">For CLR backing, the `x:Int16` primitive corresponds to <xref:System.Int16> and `x:Int16` is treated as signed.</span></span> <span data-ttu-id="594fc-149">在 XAML 中，文字語法中沒有加號 (`+`) 隱含為正數的帶正負號值。</span><span class="sxs-lookup"><span data-stu-id="594fc-149">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="594fc-150">如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.11 和 5.4.5 節](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="594fc-150">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.11 and 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint32"></a><span data-ttu-id="594fc-151">x:Int32</span><span class="sxs-lookup"><span data-stu-id="594fc-151">x:Int32</span></span>  
 <span data-ttu-id="594fc-152">對於 CLR 支援， `x:Int32` 基本類型對應至 <xref:System.Int32>。</span><span class="sxs-lookup"><span data-stu-id="594fc-152">For CLR backing, the `x:Int32` primitive corresponds to <xref:System.Int32>.</span></span> <span data-ttu-id="594fc-153">`x:Int32` 視為帶正負號。</span><span class="sxs-lookup"><span data-stu-id="594fc-153">`x:Int32` is treated as signed.</span></span> <span data-ttu-id="594fc-154">在 XAML 中，文字語法中沒有加號 (`+`) 隱含為正數的帶正負號值。</span><span class="sxs-lookup"><span data-stu-id="594fc-154">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="594fc-155">如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.12 和 5.4.6 節](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="594fc-155">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.12 and 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xint64"></a><span data-ttu-id="594fc-156">x:Int64</span><span class="sxs-lookup"><span data-stu-id="594fc-156">x:Int64</span></span>  
 <span data-ttu-id="594fc-157">對於 CLR 支援， `x:Int64` 基本類型對應至 <xref:System.Int64>。</span><span class="sxs-lookup"><span data-stu-id="594fc-157">For CLR backing, the `x:Int64` primitive corresponds to <xref:System.Int64>.</span></span> <span data-ttu-id="594fc-158">`x:Int64` 視為帶正負號。</span><span class="sxs-lookup"><span data-stu-id="594fc-158">`x:Int64` is treated as signed.</span></span> <span data-ttu-id="594fc-159">在 XAML 中，文字語法中沒有加號 (`+`) 隱含為正數的帶正負號值。</span><span class="sxs-lookup"><span data-stu-id="594fc-159">In XAML, the absence of a plus (`+`) sign in text syntax is implied as a positive signed value.</span></span>  
  
 <span data-ttu-id="594fc-160">如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.13 和 5.4.7 節](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="594fc-160">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.13 and 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xtimespan"></a><span data-ttu-id="594fc-161">x:TimeSpan</span><span class="sxs-lookup"><span data-stu-id="594fc-161">x:TimeSpan</span></span>  
 <span data-ttu-id="594fc-162">對於 CLR 支援， `x:TimeSpan` 基本類型對應至 <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="594fc-162">For CLR backing, the `x:TimeSpan` primitive corresponds to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="594fc-163">請注意，時間-日期 (time-date) 格式的 XAML 剖析原本是在 `en-US` 文化特性下執行。</span><span class="sxs-lookup"><span data-stu-id="594fc-163">Note that XAML parsing for time-date format is inherently done under `en-US` culture.</span></span>  
  
 <span data-ttu-id="594fc-164">如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.16 和 5.4.10 節](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="594fc-164">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.16 and 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xuri"></a><span data-ttu-id="594fc-165">x:Uri</span><span class="sxs-lookup"><span data-stu-id="594fc-165">x:Uri</span></span>  
 <span data-ttu-id="594fc-166">對於 CLR 支援， `x:Uri` 基本類型對應至 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="594fc-166">For CLR backing, the `x:Uri` primitive corresponds to <xref:System.Uri>.</span></span>  
  
 <span data-ttu-id="594fc-167">檢查通訊協定是否為 `x:Uri`之 XAML 定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="594fc-167">Checking for protocols is not part of the XAML definition for `x:Uri`.</span></span>  
  
 <span data-ttu-id="594fc-168">如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.15 和 5.4.9 節](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="594fc-168">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.15 and 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xbyte"></a><span data-ttu-id="594fc-169">x:Byte</span><span class="sxs-lookup"><span data-stu-id="594fc-169">x:Byte</span></span>  
 <span data-ttu-id="594fc-170">對於 CLR 支援， `x:Byte` 基本類型對應至 <xref:System.Byte>。</span><span class="sxs-lookup"><span data-stu-id="594fc-170">For CLR backing, the `x:Byte` primitive corresponds to <xref:System.Byte>.</span></span> <span data-ttu-id="594fc-171">A <xref:System.Byte>  /  `x:Byte`處理為不帶正負號。</span><span class="sxs-lookup"><span data-stu-id="594fc-171">A <xref:System.Byte> / `x:Byte` is treated as unsigned.</span></span>  
  
 <span data-ttu-id="594fc-172">如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.10 和 5.4.4 節](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="594fc-172">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.10 and 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
### <a name="xarray"></a><span data-ttu-id="594fc-173">x:Array</span><span class="sxs-lookup"><span data-stu-id="594fc-173">x:Array</span></span>  
 <span data-ttu-id="594fc-174">對於 CLR 支援， `x:Array` 基本類型對應至 <xref:System.Array>。</span><span class="sxs-lookup"><span data-stu-id="594fc-174">For CLR backing, the `x:Array` primitive corresponds to <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="594fc-175">使用標記延伸語法，即可在 XAML 2006 中定義陣列；不過，XAML 2009 語法是不需要存取標記延伸的語言定義基本類型。</span><span class="sxs-lookup"><span data-stu-id="594fc-175">You can define an array in XAML 2006  by using a markup extension syntax; however, the XAML 2009 syntax is a language-defined primitive that does not require accessing a markup extension.</span></span> <span data-ttu-id="594fc-176">如需 XAML 2006 支援的詳細資訊，請參閱 [x:Array Markup Extension](../../../docs/framework/xaml-services/x-array-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="594fc-176">For more information about XAML 2006 support, see [x:Array Markup Extension](../../../docs/framework/xaml-services/x-array-markup-extension.md).</span></span>  
  
 <span data-ttu-id="594fc-177">如需 XAML 語言規格定義，請參閱[ \[MS XAML\] 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="594fc-177">For the XAML language specification definition, see [\[MS-XAML\] Sections 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a><span data-ttu-id="594fc-178">WPF 支援</span><span class="sxs-lookup"><span data-stu-id="594fc-178">WPF Support</span></span>  
 <span data-ttu-id="594fc-179">在 WPF 中，您可以使用 XAML 2009 功能，但只能針對未編譯標記的 XAML。</span><span class="sxs-lookup"><span data-stu-id="594fc-179">In WPF, you can use XAML 2009 features but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="594fc-180">WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="594fc-180">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="594fc-181">您可以在其中使用 XAML 2009 功能與 WPF 的情況是您編寫鬆散的 XAML，然後將該 XAML 載入 WPF 執行階段和物件圖與至<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="594fc-181">A scenario where you can use XAML 2009 features together with WPF is if you author loose XAML and you then load that XAML into a WPF runtime and object graph with <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="594fc-182">WPF<xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType>及其<xref:System.Windows.Markup.XamlReader.Load%2A>可以 XAML 2009 語言關鍵字和功能處理為有效的物件圖表示法。</span><span class="sxs-lookup"><span data-stu-id="594fc-182">The WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and its <xref:System.Windows.Markup.XamlReader.Load%2A> can process XAML 2009 language keywords and features into a valid object graph representation.</span></span>
