---
title: "基礎資料類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- elementary data types
- data types [Visual Basic], elementary
ms.assetid: dfad6fe9-2da6-49a4-b0b1-2d7ae0283de5
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6d363fdd7f7f2755aec34dfe82e38d83ba6e56af
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="elementary-data-types-visual-basic"></a><span data-ttu-id="130eb-102">基礎資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="130eb-102">Elementary Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="130eb-103">提供一組預先定義的資料型別，可用於許多程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="130eb-103"> supplies a set of predefined data types, which you can use for many of your programming elements.</span></span> <span data-ttu-id="130eb-104">本章節描述這些類型，以及如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="130eb-104">This section describes these types and how to use them.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="130eb-105">在 Visual Basic 中的每個基本資料型別支援的結構或類別中<xref:System>命名空間。</xref:System></span><span class="sxs-lookup"><span data-stu-id="130eb-105">Every elementary data type in Visual Basic is supported by a structure or a class that is in the <xref:System> namespace.</span></span> <span data-ttu-id="130eb-106">編譯器會使用每個資料型別關鍵字做為別名的基礎結構或類別。</span><span class="sxs-lookup"><span data-stu-id="130eb-106">The compiler uses each data type keyword as an alias for the underlying structure or class.</span></span> <span data-ttu-id="130eb-107">例如，使用保留的字宣告變數`Byte`等同於宣告使用完整的結構名稱<xref:System.Byte?displayProperty=fullName>.</xref:System.Byte?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="130eb-107">For example, declaring a variable by using the reserved word `Byte` is the same as declaring it by using the fully qualified structure name <xref:System.Byte?displayProperty=fullName>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="130eb-108">本章節內容</span><span class="sxs-lookup"><span data-stu-id="130eb-108">In This Section</span></span>  
 [<span data-ttu-id="130eb-109">數值資料類型</span><span class="sxs-lookup"><span data-stu-id="130eb-109">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 <span data-ttu-id="130eb-110">描述整數和非整數數值類型。</span><span class="sxs-lookup"><span data-stu-id="130eb-110">Describes the integral and non-integral numeric types.</span></span>  
  
 [<span data-ttu-id="130eb-111">字元資料類型</span><span class="sxs-lookup"><span data-stu-id="130eb-111">Character Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 <span data-ttu-id="130eb-112">描述`Char`和`String`型別。</span><span class="sxs-lookup"><span data-stu-id="130eb-112">Describes the `Char` and `String` types.</span></span>  
  
 [<span data-ttu-id="130eb-113">其他資料類型</span><span class="sxs-lookup"><span data-stu-id="130eb-113">Miscellaneous Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)  
 <span data-ttu-id="130eb-114">描述`Boolean`， `Date`，和`Object`型別。</span><span class="sxs-lookup"><span data-stu-id="130eb-114">Describes the `Boolean`, `Date`, and `Object` types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="130eb-115">相關章節</span><span class="sxs-lookup"><span data-stu-id="130eb-115">Related Sections</span></span>  
 [<span data-ttu-id="130eb-116">資料類型</span><span class="sxs-lookup"><span data-stu-id="130eb-116">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="130eb-117">介紹[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]資料型別，並說明如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="130eb-117">Introduces the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="130eb-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="130eb-118">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="130eb-119">提供概觀，所提供的基本資料型別[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="130eb-119">Provides an overview of the elementary data types supplied by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>
