---
title: 如何：在 Visual Basic 中使用 StringBuilder 建立字串
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 19e036abc9d25ec7fdfd6c33ebb420ec4f503cbc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700099"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="b9999-102">如何：在 Visual Basic 中使用 StringBuilder 建立字串</span><span class="sxs-lookup"><span data-stu-id="b9999-102">How to: create strings using a StringBuilder in Visual Basic</span></span>

<span data-ttu-id="b9999-103">這個範例會使用 <xref:System.Text.StringBuilder> 類別，從許多較小的字串中，建立一個長字串。</span><span class="sxs-lookup"><span data-stu-id="b9999-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="b9999-104">@No__t 0 類別比串連許多字串的 `&=` 運算子更有效率。</span><span class="sxs-lookup"><span data-stu-id="b9999-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>

## <a name="example"></a><span data-ttu-id="b9999-105">範例</span><span class="sxs-lookup"><span data-stu-id="b9999-105">Example</span></span>

<span data-ttu-id="b9999-106">下列範例會建立 @no__t 0 類別的實例，並將1000字串附加至該實例，然後傳回其字串表示：</span><span class="sxs-lookup"><span data-stu-id="b9999-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span></span>

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a><span data-ttu-id="b9999-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9999-107">See also</span></span>

- [<span data-ttu-id="b9999-108">使用 StringBuilder 類別</span><span class="sxs-lookup"><span data-stu-id="b9999-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="b9999-109">&= 運算子</span><span class="sxs-lookup"><span data-stu-id="b9999-109">&= Operator</span></span>](../../../language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="b9999-110">字串</span><span class="sxs-lookup"><span data-stu-id="b9999-110">Strings</span></span>](index.md)
- [<span data-ttu-id="b9999-111">建立新字串</span><span class="sxs-lookup"><span data-stu-id="b9999-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="b9999-112">操作字串</span><span class="sxs-lookup"><span data-stu-id="b9999-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
