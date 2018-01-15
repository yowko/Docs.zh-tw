---
title: "使用 .NET Compiler Platform SDK 語意模型"
description: "此概觀可讓您了解用來了解和管理程式碼語意模型的類型。"
author: billwagner
ms.author: wiwagn
ms.date: 10/15/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 28366093c516f5367d82c0bdfc53749e764361ef
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2017
---
# <a name="work-with-semantics"></a><span data-ttu-id="56a46-103">使用語意</span><span class="sxs-lookup"><span data-stu-id="56a46-103">Work with semantics</span></span>

<span data-ttu-id="56a46-104">[語法樹狀結構](work-with-syntax.md)代表原始程式碼的語彙和語法結構。</span><span class="sxs-lookup"><span data-stu-id="56a46-104">[Syntax trees](work-with-syntax.md) represent the lexical and syntactic structure of source code.</span></span> <span data-ttu-id="56a46-105">雖然只要這項資訊就足以描述來源中的所有宣告和邏輯，但其資訊卻不足以識別所要參考的項目。</span><span class="sxs-lookup"><span data-stu-id="56a46-105">Although this information alone is enough to describe all the declarations and logic in the source, it is not enough information to identify what is being referenced.</span></span> <span data-ttu-id="56a46-106">名稱可能代表：</span><span class="sxs-lookup"><span data-stu-id="56a46-106">A name may represent:</span></span>

- <span data-ttu-id="56a46-107">類型</span><span class="sxs-lookup"><span data-stu-id="56a46-107">a type</span></span>
- <span data-ttu-id="56a46-108">欄位</span><span class="sxs-lookup"><span data-stu-id="56a46-108">a field</span></span>
- <span data-ttu-id="56a46-109">方法</span><span class="sxs-lookup"><span data-stu-id="56a46-109">a method</span></span>
- <span data-ttu-id="56a46-110">區域變數</span><span class="sxs-lookup"><span data-stu-id="56a46-110">a local variable</span></span>

<span data-ttu-id="56a46-111">雖然上述所有項目都是唯一且不同的，但是判斷識別碼實際所參考的項目通常需要深入了解語言規則。</span><span class="sxs-lookup"><span data-stu-id="56a46-111">Although each of these is uniquely different, determining which one an identifier actually refers to often requires a deep understanding of the language rules.</span></span> 

<span data-ttu-id="56a46-112">原始程式碼中具有程式項目，而且程式也可以參考以組件檔封裝的先前已編譯程式庫。</span><span class="sxs-lookup"><span data-stu-id="56a46-112">There are program elements represented in source code, and programs can also refer to previously compiled libraries, packaged in assembly files.</span></span> <span data-ttu-id="56a46-113">雖然沒有原始程式碼可用於組件，因而沒有語法節點或樹狀結構，但是程式仍然可以參考其內的項目。</span><span class="sxs-lookup"><span data-stu-id="56a46-113">Although no source code, and therefore no syntax nodes or trees, are available for assemblies, programs can still refer to elements inside them.</span></span>

<span data-ttu-id="56a46-114">針對這些工作，您需要**語意模型**。</span><span class="sxs-lookup"><span data-stu-id="56a46-114">For those tasks, you need the **Semantic model**.</span></span>

<span data-ttu-id="56a46-115">除了原始程式碼的語法模型之外，語意模型還會封裝語言規則，讓您輕鬆且正確地比對識別碼與所參考的正確程式項目。</span><span class="sxs-lookup"><span data-stu-id="56a46-115">In addition to a syntactic model of the source code, a semantic model encapsulates the language rules, giving you an easy way to correctly match identifiers with the correct program element being referenced.</span></span>

## <a name="compilation"></a><span data-ttu-id="56a46-116">編譯</span><span class="sxs-lookup"><span data-stu-id="56a46-116">Compilation</span></span>

<span data-ttu-id="56a46-117">編譯會呈現編譯 C# 或 Visual Basic 程式所需的所有項目，以包含所有組件參考、編譯器選項和原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="56a46-117">A compilation is a representation of everything needed to compile a C# or Visual Basic program, which includes all the assembly references, compiler options, and source files.</span></span> 

<span data-ttu-id="56a46-118">因為所有這些資訊都是在同一個地方，所以可以詳細描述原始程式碼中包含的項目。</span><span class="sxs-lookup"><span data-stu-id="56a46-118">Because all this information is in one place, the elements contained in the source code can be described in more detail.</span></span> <span data-ttu-id="56a46-119">編譯會將每個宣告類型、成員或變數呈現為符號。</span><span class="sxs-lookup"><span data-stu-id="56a46-119">The compilation represents each declared type, member, or variable as a symbol.</span></span> <span data-ttu-id="56a46-120">編譯包含各種方法，協助您尋找並關聯已宣告於原始程式碼或從組件中匯入為中繼資料的符號。</span><span class="sxs-lookup"><span data-stu-id="56a46-120">The compilation contains a variety of methods that help you find and relate the symbols that have either been declared in the source code or imported as metadata from an assembly.</span></span>

<span data-ttu-id="56a46-121">與語法樹狀結構類似，編譯為不可變。</span><span class="sxs-lookup"><span data-stu-id="56a46-121">Similar to syntax trees, compilations are immutable.</span></span> <span data-ttu-id="56a46-122">建立編譯之後，您或可能與其共用的其他人就無法變更它。</span><span class="sxs-lookup"><span data-stu-id="56a46-122">After you create a compilation, it cannot be changed by you or anyone else you might be sharing it with.</span></span> <span data-ttu-id="56a46-123">不過，您可以從現有編譯建立新的編譯，並指定這麼做的變更。</span><span class="sxs-lookup"><span data-stu-id="56a46-123">However, you can create a new compilation from an existing compilation, specifying a change as you do so.</span></span> <span data-ttu-id="56a46-124">例如，您可以建立與現有編譯完全相同的編譯，差異在於它可以包含其他原始程式檔或組件參考。</span><span class="sxs-lookup"><span data-stu-id="56a46-124">For example, you might create a compilation that is the same in every way as an existing compilation, except it may include an additional source file or assembly reference.</span></span>

## <a name="symbols"></a><span data-ttu-id="56a46-125">Symbol</span><span class="sxs-lookup"><span data-stu-id="56a46-125">Symbols</span></span>

<span data-ttu-id="56a46-126">符號代表由原始程式碼所宣告或從組件中匯入為中繼資料的相異項目。</span><span class="sxs-lookup"><span data-stu-id="56a46-126">A symbol represents a distinct element declared by the source code or imported from an assembly as metadata.</span></span> <span data-ttu-id="56a46-127">每個命名空間、類型、方法、屬性、欄位、事件、參數或區域變數都是以符號呈現。</span><span class="sxs-lookup"><span data-stu-id="56a46-127">Every namespace, type, method, property, field, event, parameter, or local variable is represented by a symbol.</span></span> 

<span data-ttu-id="56a46-128"><xref:Microsoft.CodeAnalysis.Compilation> 類型上的各種不同方法和屬性可協助您尋找符號。</span><span class="sxs-lookup"><span data-stu-id="56a46-128">A variety of methods and properties on the <xref:Microsoft.CodeAnalysis.Compilation> type help you find symbols.</span></span> <span data-ttu-id="56a46-129">例如，您可以依其一般中繼資料名稱來找到已宣告類型的符號。</span><span class="sxs-lookup"><span data-stu-id="56a46-129">For example, you can find a symbol for a declared type by its common metadata name.</span></span> <span data-ttu-id="56a46-130">您也可以存取整個符號表作為全域命名空間之根符號的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="56a46-130">You can also access the entire symbol table as a tree of symbols rooted by the global namespace.</span></span>

<span data-ttu-id="56a46-131">符號也會包含編譯器從來源或中繼資料判斷而來的其他資訊，例如其他參考的符號。</span><span class="sxs-lookup"><span data-stu-id="56a46-131">Symbols also contain additional information that the compiler determines from the source or metadata, such as other referenced symbols.</span></span> <span data-ttu-id="56a46-132">每種符號都是由衍生自 <xref:Microsoft.CodeAnalysis.ISymbol> 的個別介面所代表，而每個介面都有詳述編譯器所收集資訊的專屬方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="56a46-132">Each kind of symbol is represented by a separate interface derived from <xref:Microsoft.CodeAnalysis.ISymbol>, each with its own methods and properties detailing the information the compiler has gathered.</span></span> <span data-ttu-id="56a46-133">其中許多屬性都是直接參考其他符號。</span><span class="sxs-lookup"><span data-stu-id="56a46-133">Many of these properties directly reference other symbols.</span></span> <span data-ttu-id="56a46-134">例如，<xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> 屬性會告知方法宣告所參考的實際類型符號。</span><span class="sxs-lookup"><span data-stu-id="56a46-134">For example, the <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> property tells you the actual type symbol that the method declaration references.</span></span>

<span data-ttu-id="56a46-135">符號會呈現原始程式碼與中繼資料間之命名空間、類型和成員的一般表示。</span><span class="sxs-lookup"><span data-stu-id="56a46-135">Symbols present a common representation of namespaces, types, and members, between source code and metadata.</span></span> <span data-ttu-id="56a46-136">例如，在原始程式碼中宣告的方法以及從中繼資料匯入的方法，都是使用具有相同屬性的 <xref:Microsoft.CodeAnalysis.IMethodSymbol> 所呈現。</span><span class="sxs-lookup"><span data-stu-id="56a46-136">For example, a method that was declared in source code and a method that was imported from metadata are both represented by an <xref:Microsoft.CodeAnalysis.IMethodSymbol> with the same properties.</span></span>

<span data-ttu-id="56a46-137">符號的概念類似 <xref:System.Reflection> API 所呈現的 CLR 類型系統，但它們不只是將類型模型化。</span><span class="sxs-lookup"><span data-stu-id="56a46-137">Symbols are similar in concept to the CLR type system as represented by the <xref:System.Reflection> API, yet they are richer in that they model more than just types.</span></span> <span data-ttu-id="56a46-138">命名空間、區域變數和標籤都是符號。</span><span class="sxs-lookup"><span data-stu-id="56a46-138">Namespaces, local variables, and labels are all symbols.</span></span> <span data-ttu-id="56a46-139">此外，符號是語言概念的呈現，而不是 CLR 概念。</span><span class="sxs-lookup"><span data-stu-id="56a46-139">In addition, symbols are a representation of language concepts, not CLR concepts.</span></span> <span data-ttu-id="56a46-140">有很多重疊，但也有許多有意義的區別。</span><span class="sxs-lookup"><span data-stu-id="56a46-140">There is a lot of overlap, but there are many meaningful distinctions as well.</span></span> <span data-ttu-id="56a46-141">例如，C# 或 Visual Basic 中的迭代器方法是單一符號。</span><span class="sxs-lookup"><span data-stu-id="56a46-141">For instance, an iterator method in C# or Visual Basic is a single symbol.</span></span> <span data-ttu-id="56a46-142">不過，迭代器方法轉譯為 CLR 中繼資料時，它就是類型和多個方法。</span><span class="sxs-lookup"><span data-stu-id="56a46-142">However, when the iterator method is translated to CLR metadata, it is a type and multiple methods.</span></span>

## <a name="semantic-model"></a><span data-ttu-id="56a46-143">語意模型</span><span class="sxs-lookup"><span data-stu-id="56a46-143">Semantic model</span></span>

<span data-ttu-id="56a46-144">語意模型代表單一原始程式檔的所有語意資訊。</span><span class="sxs-lookup"><span data-stu-id="56a46-144">A semantic model represents all the semantic information for a single source file.</span></span> <span data-ttu-id="56a46-145">您可以使用它來探索下列項目：</span><span class="sxs-lookup"><span data-stu-id="56a46-145">You can use it to discover the following:</span></span> 

* <span data-ttu-id="56a46-146">來源中特定位置所參考的符號。</span><span class="sxs-lookup"><span data-stu-id="56a46-146">The symbols referenced at a specific location in source.</span></span>
* <span data-ttu-id="56a46-147">任何運算式的結果類型。</span><span class="sxs-lookup"><span data-stu-id="56a46-147">The resultant type of any expression.</span></span>
* <span data-ttu-id="56a46-148">所有診斷，也就是錯誤和警告。</span><span class="sxs-lookup"><span data-stu-id="56a46-148">All diagnostics, which are errors and warnings.</span></span>
* <span data-ttu-id="56a46-149">變數如何流入和流出來源的區域。</span><span class="sxs-lookup"><span data-stu-id="56a46-149">How variables flow in and out of regions of source.</span></span>
* <span data-ttu-id="56a46-150">更推測性問題的答案。</span><span class="sxs-lookup"><span data-stu-id="56a46-150">The answers to more speculative questions.</span></span>
