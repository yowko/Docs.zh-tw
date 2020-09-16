---
description: 部分型別 - C# 參考
title: 部分型別 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 0445ac33473c7e2d1916705893b22ba21bb981ff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536842"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="7ae3c-103">部分型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="7ae3c-103">partial type (C# Reference)</span></span>

<span data-ttu-id="7ae3c-104">部分型別定義允許將類別、結構或介面定義分割成多個檔案。</span><span class="sxs-lookup"><span data-stu-id="7ae3c-104">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="7ae3c-105">在 *File1.cs*中：</span><span class="sxs-lookup"><span data-stu-id="7ae3c-105">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="7ae3c-106">在 *File2.cs* 中，宣告：</span><span class="sxs-lookup"><span data-stu-id="7ae3c-106">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="7ae3c-107">備註</span><span class="sxs-lookup"><span data-stu-id="7ae3c-107">Remarks</span></span>

<span data-ttu-id="7ae3c-108">將類別、結構或介面型別分割成數個檔案在處理大型專案，或者處理自動產生的程式碼，例如 [Windows Forms 設計工具](/dotnet/desktop/winforms/controls/developing-windows-forms-controls-at-design-time)提供的程式碼時，會很有用。</span><span class="sxs-lookup"><span data-stu-id="7ae3c-108">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](/dotnet/desktop/winforms/controls/developing-windows-forms-controls-at-design-time).</span></span> <span data-ttu-id="7ae3c-109">部分類別可包含[部分方法](partial-method.md)。</span><span class="sxs-lookup"><span data-stu-id="7ae3c-109">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="7ae3c-110">如需詳細資訊，請參閱[部分類別和方法](../../programming-guide/classes-and-structs/partial-classes-and-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="7ae3c-110">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7ae3c-111">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="7ae3c-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7ae3c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ae3c-112">See also</span></span>

- [<span data-ttu-id="7ae3c-113">C # 參考</span><span class="sxs-lookup"><span data-stu-id="7ae3c-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7ae3c-114">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7ae3c-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7ae3c-115">修飾詞</span><span class="sxs-lookup"><span data-stu-id="7ae3c-115">Modifiers</span></span>](index.md)
- [<span data-ttu-id="7ae3c-116">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="7ae3c-116">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
