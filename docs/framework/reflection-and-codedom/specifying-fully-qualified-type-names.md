---
title: "指定完整的類型名稱"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- Backus-Naur form
- languages, BNF grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6759e7b62f4083f6d53663385398baf098f2676f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="8c0d6-102">指定完整的類型名稱</span><span class="sxs-lookup"><span data-stu-id="8c0d6-102">Specifying Fully Qualified Type Names</span></span>
<span data-ttu-id="8c0d6-103">您必須指定具有各種反映作業有效輸入的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="8c0d6-104">完整的類型名稱包括組件名稱規格、命名空間規格和類型名稱。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="8c0d6-105">方法使用的類型名稱規格如 <xref:System.Type.GetType%2A?displayProperty=nameWithType>、<xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>、<xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> 和 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="backus-naur-form-grammar-for-type-names"></a><span data-ttu-id="8c0d6-106">類型名稱的巴克斯格式文法</span><span class="sxs-lookup"><span data-stu-id="8c0d6-106">Backus-Naur Form Grammar for Type Names</span></span>  
 <span data-ttu-id="8c0d6-107">巴克斯格式 (BNF) 會定義形式語言的語法。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-107">The Backus-Naur form (BNF) defines the syntax of formal languages.</span></span> <span data-ttu-id="8c0d6-108">下表列出 BNF 語彙規則，說明如何辨識有效的輸入。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-108">The following table lists BNF lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="8c0d6-109">終端項 (不會進一步縮減的那些項目) 全部以大寫字母顯示。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="8c0d6-110">非終端項 (會進一步縮減的那些項目) 會以大小寫混合或單引號括住的字串顯示，但單引號 (') 不是語法本身的一部分。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="8c0d6-111">縱線字元 (&#124;) 表示具有子規則的規則。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>  
  
|<span data-ttu-id="8c0d6-112">完整類型名稱的 BNF 文法</span><span class="sxs-lookup"><span data-stu-id="8c0d6-112">BNF grammar of fully qualified type names</span></span>|  
|-----------------------------------------------|  
|<span data-ttu-id="8c0d6-113">TypeSpec                          :=   ReferenceTypeSpec</span><span class="sxs-lookup"><span data-stu-id="8c0d6-113">TypeSpec                          :=   ReferenceTypeSpec</span></span><br /><br /> <span data-ttu-id="8c0d6-114">&#124;     SimpleTypeSpec</span><span class="sxs-lookup"><span data-stu-id="8c0d6-114">&#124;     SimpleTypeSpec</span></span>|  
|<span data-ttu-id="8c0d6-115">ReferenceTypeSpec            :=   SimpleTypeSpec '&'</span><span class="sxs-lookup"><span data-stu-id="8c0d6-115">ReferenceTypeSpec            :=   SimpleTypeSpec '&'</span></span>|  
|<span data-ttu-id="8c0d6-116">SimpleTypeSpec                :=   PointerTypeSpec</span><span class="sxs-lookup"><span data-stu-id="8c0d6-116">SimpleTypeSpec                :=   PointerTypeSpec</span></span><br /><br /> <span data-ttu-id="8c0d6-117">&#124;     ArrayTypeSpec</span><span class="sxs-lookup"><span data-stu-id="8c0d6-117">&#124;     ArrayTypeSpec</span></span><br /><br /> <span data-ttu-id="8c0d6-118">&#124;     TypeName</span><span class="sxs-lookup"><span data-stu-id="8c0d6-118">&#124;     TypeName</span></span>|  
|<span data-ttu-id="8c0d6-119">PointerTypeSpec                :=   SimpleTypeSpec '*'</span><span class="sxs-lookup"><span data-stu-id="8c0d6-119">PointerTypeSpec                :=   SimpleTypeSpec '*'</span></span>|  
|<span data-ttu-id="8c0d6-120">ArrayTypeSpec                  :=   SimpleTypeSpec '[ReflectionDimension]'</span><span class="sxs-lookup"><span data-stu-id="8c0d6-120">ArrayTypeSpec                  :=   SimpleTypeSpec '[ReflectionDimension]'</span></span><br /><br /> <span data-ttu-id="8c0d6-121">&#124;     SimpleTypeSpec '[ReflectionEmitDimension]'</span><span class="sxs-lookup"><span data-stu-id="8c0d6-121">&#124;     SimpleTypeSpec '[ReflectionEmitDimension]'</span></span>|  
|<span data-ttu-id="8c0d6-122">ReflectionDimension           :=   '*'</span><span class="sxs-lookup"><span data-stu-id="8c0d6-122">ReflectionDimension           :=   '*'</span></span><br /><br /> <span data-ttu-id="8c0d6-123">&#124;     ReflectionDimension ',' ReflectionDimension</span><span class="sxs-lookup"><span data-stu-id="8c0d6-123">&#124;     ReflectionDimension ',' ReflectionDimension</span></span><br /><br /> <span data-ttu-id="8c0d6-124">&#124;     NOTOKEN</span><span class="sxs-lookup"><span data-stu-id="8c0d6-124">&#124;     NOTOKEN</span></span>|  
|<span data-ttu-id="8c0d6-125">ReflectionEmitDimension    :=   '*'</span><span class="sxs-lookup"><span data-stu-id="8c0d6-125">ReflectionEmitDimension    :=   '*'</span></span><br /><br /> <span data-ttu-id="8c0d6-126">&#124;     Number '..'</span><span class="sxs-lookup"><span data-stu-id="8c0d6-126">&#124;     Number '..'</span></span> <span data-ttu-id="8c0d6-127">數字</span><span class="sxs-lookup"><span data-stu-id="8c0d6-127">Number</span></span><br /><br /> <span data-ttu-id="8c0d6-128">&#124;     Number '…'</span><span class="sxs-lookup"><span data-stu-id="8c0d6-128">&#124;     Number '…'</span></span><br /><br /> <span data-ttu-id="8c0d6-129">&#124;     ReflectionDimension ',' ReflectionDimension</span><span class="sxs-lookup"><span data-stu-id="8c0d6-129">&#124;     ReflectionDimension ',' ReflectionDimension</span></span><br /><br /> <span data-ttu-id="8c0d6-130">&#124;     NOTOKEN</span><span class="sxs-lookup"><span data-stu-id="8c0d6-130">&#124;     NOTOKEN</span></span>|  
|<span data-ttu-id="8c0d6-131">Number                            :=   [0-9]+</span><span class="sxs-lookup"><span data-stu-id="8c0d6-131">Number                            :=   [0-9]+</span></span>|  
|<span data-ttu-id="8c0d6-132">TypeName                         :=   NamespaceTypeName</span><span class="sxs-lookup"><span data-stu-id="8c0d6-132">TypeName                         :=   NamespaceTypeName</span></span><br /><br /> <span data-ttu-id="8c0d6-133">&#124;     NamespaceTypeName ',' AssemblyNameSpec</span><span class="sxs-lookup"><span data-stu-id="8c0d6-133">&#124;     NamespaceTypeName ',' AssemblyNameSpec</span></span>|  
|<span data-ttu-id="8c0d6-134">NamespaceTypeName        :=   NestedTypeName</span><span class="sxs-lookup"><span data-stu-id="8c0d6-134">NamespaceTypeName        :=   NestedTypeName</span></span><br /><br /> <span data-ttu-id="8c0d6-135">&#124;     NamespaceSpec '.'NestedTypeName</span><span class="sxs-lookup"><span data-stu-id="8c0d6-135">&#124;     NamespaceSpec '.' NestedTypeName</span></span>|  
|<span data-ttu-id="8c0d6-136">NestedTypeName               :=   IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="8c0d6-136">NestedTypeName               :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="8c0d6-137">&#124;     NestedTypeName '+' IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="8c0d6-137">&#124;     NestedTypeName '+' IDENTIFIER</span></span>|  
|<span data-ttu-id="8c0d6-138">NamespaceSpec                 :=   IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="8c0d6-138">NamespaceSpec                 :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="8c0d6-139">&#124;     NamespaceSpec '.'IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="8c0d6-139">&#124;     NamespaceSpec '.' IDENTIFIER</span></span>|  
|<span data-ttu-id="8c0d6-140">AssemblyNameSpec           :=   IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="8c0d6-140">AssemblyNameSpec           :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="8c0d6-141">&#124;     IDENTIFIER ',' AssemblyProperties</span><span class="sxs-lookup"><span data-stu-id="8c0d6-141">&#124;     IDENTIFIER ',' AssemblyProperties</span></span>|  
|<span data-ttu-id="8c0d6-142">AssemblyProperties            :=   AssemblyProperty</span><span class="sxs-lookup"><span data-stu-id="8c0d6-142">AssemblyProperties            :=   AssemblyProperty</span></span><br /><br /> <span data-ttu-id="8c0d6-143">&#124;     AssemblyProperties ',' AssemblyProperty</span><span class="sxs-lookup"><span data-stu-id="8c0d6-143">&#124;     AssemblyProperties ',' AssemblyProperty</span></span>|  
|<span data-ttu-id="8c0d6-144">AssemblyProperty              :=   AssemblyPropertyName '=' AssemblyPropertyValue</span><span class="sxs-lookup"><span data-stu-id="8c0d6-144">AssemblyProperty              :=   AssemblyPropertyName '=' AssemblyPropertyValue</span></span>|  
  
## <a name="specifying-special-characters"></a><span data-ttu-id="8c0d6-145">指定特殊字元</span><span class="sxs-lookup"><span data-stu-id="8c0d6-145">Specifying Special Characters</span></span>  
 <span data-ttu-id="8c0d6-146">類型名稱中的 IDENTIFIER 是語言規則判定的任何有效名稱。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-146">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>  
  
 <span data-ttu-id="8c0d6-147">將反斜線 (\\) 用作逸出字元，分隔下列作為 IDENTIFIER 一部分的權杖。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-147">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>  
  
|<span data-ttu-id="8c0d6-148">語彙基元</span><span class="sxs-lookup"><span data-stu-id="8c0d6-148">Token</span></span>|<span data-ttu-id="8c0d6-149">意義</span><span class="sxs-lookup"><span data-stu-id="8c0d6-149">Meaning</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="8c0d6-150">\\,</span><span class="sxs-lookup"><span data-stu-id="8c0d6-150">\\,</span></span>|<span data-ttu-id="8c0d6-151">組件分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-151">Assembly separator.</span></span>|  
|\\+|<span data-ttu-id="8c0d6-152">巢狀型別分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-152">Nested type separator.</span></span>|  
|\\&|<span data-ttu-id="8c0d6-153">參考型別。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-153">Reference type.</span></span>|  
|\\*|<span data-ttu-id="8c0d6-154">指標類型。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-154">Pointer type.</span></span>|  
|<span data-ttu-id="8c0d6-155">\\[</span><span class="sxs-lookup"><span data-stu-id="8c0d6-155">\\[</span></span>|<span data-ttu-id="8c0d6-156">陣列維度分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-156">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="8c0d6-157">\\]</span><span class="sxs-lookup"><span data-stu-id="8c0d6-157">\\]</span></span>|<span data-ttu-id="8c0d6-158">陣列維度分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-158">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="8c0d6-159">\\.</span><span class="sxs-lookup"><span data-stu-id="8c0d6-159">\\.</span></span>|<span data-ttu-id="8c0d6-160">句號只有用在陣列規格中時，前面才會使用反斜線。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-160">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="8c0d6-161">NamespaceSpec 中的句號不接受反斜線。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-161">Periods in NamespaceSpec do not take the backslash.</span></span>|  
|\\\|<span data-ttu-id="8c0d6-162">反斜線會視需要當成字串常值。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-162">Backslash when needed as a string literal.</span></span>|  
  
 <span data-ttu-id="8c0d6-163">請注意，除 AssemblyNameSpec 以外的所有 TypeSpec 元件中，空格都是相關的。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-163">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="8c0d6-164">在 AssemblyNameSpec 中，',' 分隔符號之前的空格是相關的，但 ',' 分隔符號之後的空格則會忽略。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-164">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>  
  
 <span data-ttu-id="8c0d6-165"><xref:System.Type.FullName%2A?displayProperty=nameWithType> 之類的反映類別會傳回損害的名稱，所以傳回的名稱可用於呼叫 <xref:System.Type.GetType%2A>，如在 `MyType.GetType(myType.FullName)` 中一樣。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-165">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>  
  
 <span data-ttu-id="8c0d6-166">例如，類型的完整名稱可能是 `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-166">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
 <span data-ttu-id="8c0d6-167">如果以前的命名空間是 `Ozzy.Out+Back`，則反斜線前面必須有加號。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-167">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="8c0d6-168">否則，剖析器會將它解譯為巢狀分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-168">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="8c0d6-169">反映將此字串發出為 `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-169">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
## <a name="specifying-assembly-names"></a><span data-ttu-id="8c0d6-170">指定組件名稱</span><span class="sxs-lookup"><span data-stu-id="8c0d6-170">Specifying Assembly Names</span></span>  
 <span data-ttu-id="8c0d6-171">組件名稱規格中的基本資訊是組件的文字名稱 (IDENTIFIER)。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-171">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="8c0d6-172">您可以按照逗號分隔的屬性/值組清單理解 IDENTIFIER，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-172">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="8c0d6-173">IDENTIFIER 的命名應依照檔案命名的規則。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-173">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="8c0d6-174">IDENTIFIER 不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-174">The IDENTIFIER is case-insensitive.</span></span>  
  
|<span data-ttu-id="8c0d6-175">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="8c0d6-175">Property name</span></span>|<span data-ttu-id="8c0d6-176">描述</span><span class="sxs-lookup"><span data-stu-id="8c0d6-176">Description</span></span>|<span data-ttu-id="8c0d6-177">允許的值</span><span class="sxs-lookup"><span data-stu-id="8c0d6-177">Allowable values</span></span>|  
|-------------------|-----------------|----------------------|  
|<span data-ttu-id="8c0d6-178">**版本**</span><span class="sxs-lookup"><span data-stu-id="8c0d6-178">**Version**</span></span>|<span data-ttu-id="8c0d6-179">組件版本號碼</span><span class="sxs-lookup"><span data-stu-id="8c0d6-179">Assembly version number</span></span>|<span data-ttu-id="8c0d6-180">在 *Major.Minor.Build.Revision* 中，*Major*、*Minor*、*Build* 和 *Revision* 是介於 0 到 65535 (含) 之間的整數。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-180">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|  
|<span data-ttu-id="8c0d6-181">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="8c0d6-181">**PublicKey**</span></span>|<span data-ttu-id="8c0d6-182">完整公開金鑰</span><span class="sxs-lookup"><span data-stu-id="8c0d6-182">Full public key</span></span>|<span data-ttu-id="8c0d6-183">十六進位格式的完整公開金鑰字串值。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-183">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="8c0d6-184">指定 null 參考 (Visual Basic 為**Nothing**) 以明確指出私用組件。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-184">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="8c0d6-185">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="8c0d6-185">**PublicKeyToken**</span></span>|<span data-ttu-id="8c0d6-186">公開金鑰語彙基元 (完整公開金鑰的 8 位元組雜湊)</span><span class="sxs-lookup"><span data-stu-id="8c0d6-186">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="8c0d6-187">十六進位格式的公開金鑰語彙基元字串值。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-187">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="8c0d6-188">指定 null 參考 (Visual Basic 為 **Nothing**) 以明確指出私用組件。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-188">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="8c0d6-189">**文化特性**</span><span class="sxs-lookup"><span data-stu-id="8c0d6-189">**Culture**</span></span>|<span data-ttu-id="8c0d6-190">組件文化特性</span><span class="sxs-lookup"><span data-stu-id="8c0d6-190">Assembly culture</span></span>|<span data-ttu-id="8c0d6-191">RFC-1766 格式的組件文化特性，或「中性的」語言無關 (非附屬) 組件。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-191">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|  
|<span data-ttu-id="8c0d6-192">**自訂**</span><span class="sxs-lookup"><span data-stu-id="8c0d6-192">**Custom**</span></span>|<span data-ttu-id="8c0d6-193">自訂二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-193">Custom binary large object (BLOB).</span></span> <span data-ttu-id="8c0d6-194">目前只用於[原生映像產生器 (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 產生的組件。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-194">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="8c0d6-195">自訂原生映像產生器工具所用的字串用於通知組件快取安裝中的組件是原生映像，因此要安裝在原生映像快取中。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-195">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="8c0d6-196">也稱為 zap 字串。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-196">Also called a zap string.</span></span>|  
  
 <span data-ttu-id="8c0d6-197">下例示範的 **AssemblyName**，僅以預設文化特性命名組件。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-197">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 <span data-ttu-id="8c0d6-198">下例顯示具有 "en" 文化特性之強式名稱組件的完整指定參考。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-198">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 <span data-ttu-id="8c0d6-199">下列範例各自都有部分指定的 **AssemblyName**，無論強式或簡單名稱組件皆可滿足。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-199">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 <span data-ttu-id="8c0d6-200">下列範例各自都有部分指定的 **AssemblyName**，必須由簡單名稱組件滿足。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-200">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 <span data-ttu-id="8c0d6-201">下列範例各自都有部分指定的 **AssemblyName**，必須由強式名稱組件滿足。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-201">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## <a name="specifying-pointers"></a><span data-ttu-id="8c0d6-202">指定指標</span><span class="sxs-lookup"><span data-stu-id="8c0d6-202">Specifying Pointers</span></span>  
 <span data-ttu-id="8c0d6-203">SimpleTypeSpec* 表示 Unmanaged 指標。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-203">SimpleTypeSpec* represents an unmanaged pointer.</span></span> <span data-ttu-id="8c0d6-204">例如，若要取得類型 MyType 的指標，請使用 `Type.GetType("MyType*")`。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-204">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="8c0d6-205">若要取得類型 MyType 指標的指標，請使用 `Type.GetType("MyType**")`。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-205">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>  
  
## <a name="specifying-references"></a><span data-ttu-id="8c0d6-206">指定參考</span><span class="sxs-lookup"><span data-stu-id="8c0d6-206">Specifying References</span></span>  
 <span data-ttu-id="8c0d6-207">SimpleTypeSpec & 代表 Managed 指標或參考。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-207">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="8c0d6-208">例如，若要取得類型 MyType 的參考，請使用 `Type.GetType("MyType &")`。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-208">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="8c0d6-209">請注意，參考與指標不同，僅限一個層級。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-209">Note that unlike pointers, references are limited to one level.</span></span>  
  
## <a name="specifying-arrays"></a><span data-ttu-id="8c0d6-210">指定陣列</span><span class="sxs-lookup"><span data-stu-id="8c0d6-210">Specifying Arrays</span></span>  
 <span data-ttu-id="8c0d6-211">在 BNF 文法中，ReflectionEmitDimension 只適用於使用 <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> 擷取的不完整類型定義。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-211">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8c0d6-212">不完整的類型定義是使用 <xref:System.Reflection.Emit?displayProperty=nameWithType> 建構卻未呼叫 <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> 的 <xref:System.Reflection.Emit.TypeBuilder> 物件。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-212">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="8c0d6-213">ReflectionDimension 可以用來擷取任何已完成的類型定義，也就是已載入的類型。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-213">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>  
  
 <span data-ttu-id="8c0d6-214">指定陣列陣序即可存取反映中的陣列：</span><span class="sxs-lookup"><span data-stu-id="8c0d6-214">Arrays are accessed in reflection by specifying the rank of the array:</span></span>  
  
-   <span data-ttu-id="8c0d6-215">`Type.GetType("MyArray[]")` 會取得下限為 0 的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-215">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>  
  
-   <span data-ttu-id="8c0d6-216">`Type.GetType("MyArray[*]")` 會取得下限不明的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-216">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>  
  
-   <span data-ttu-id="8c0d6-217">`Type.GetType("MyArray[][]")` 會取得二維陣列的陣列。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-217">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>  
  
-   <span data-ttu-id="8c0d6-218">`Type.GetType("MyArray[*,*]")` 和 `Type.GetType("MyArray[,]")` 會取得下限不明的矩形二維陣列。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-218">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>  
  
 <span data-ttu-id="8c0d6-219">請注意，就執行階段而言是 `MyArray[] != MyArray[*]`，但對多維陣列而言，兩種標記法是一樣的。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-219">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="8c0d6-220">亦即 `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` 評估為 **true**。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-220">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>  
  
 <span data-ttu-id="8c0d6-221">對 **ModuleBuilder.GetType** 而言，`MyArray[0..5]` 表示大小 6、下限 0 的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-221">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="8c0d6-222">`MyArray[4…]` 表示大小不明、下限 4 的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="8c0d6-222">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c0d6-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c0d6-223">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 <xref:System.Reflection.Emit.ModuleBuilder>  
 <xref:System.Reflection.Emit.TypeBuilder>  
 <xref:System.Type.FullName%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="8c0d6-224">檢視類型資訊</span><span class="sxs-lookup"><span data-stu-id="8c0d6-224">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
