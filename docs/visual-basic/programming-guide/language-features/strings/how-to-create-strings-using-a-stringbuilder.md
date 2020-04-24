---
title: 如何:使用字串產生器建立字串
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: c41db584df83782dab99b90043045aa2cabcb6ff
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645331"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="7e49b-102">如何:在視覺化基礎使用字串產生器建立字串</span><span class="sxs-lookup"><span data-stu-id="7e49b-102">How to: create strings using a StringBuilder in Visual Basic</span></span>

<span data-ttu-id="7e49b-103">此示例使用<xref:System.Text.StringBuilder>類從許多較小的字串構造長字串。</span><span class="sxs-lookup"><span data-stu-id="7e49b-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="7e49b-104">類<xref:System.Text.StringBuilder>`&=`比 運算串聯許多字串更有效。</span><span class="sxs-lookup"><span data-stu-id="7e49b-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>

## <a name="example"></a><span data-ttu-id="7e49b-105">範例</span><span class="sxs-lookup"><span data-stu-id="7e49b-105">Example</span></span>

<span data-ttu-id="7e49b-106">下面的範例建立類的<xref:System.Text.StringBuilder>實體,將 1,000 個字串附加到該實體,然後傳回其字串表示形式:</span><span class="sxs-lookup"><span data-stu-id="7e49b-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span></span>

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a><span data-ttu-id="7e49b-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e49b-107">See also</span></span>

- [<span data-ttu-id="7e49b-108">使用 StringBuilder 類別</span><span class="sxs-lookup"><span data-stu-id="7e49b-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="7e49b-109">&= 運算子</span><span class="sxs-lookup"><span data-stu-id="7e49b-109">&= Operator</span></span>](../../../language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="7e49b-110">字串</span><span class="sxs-lookup"><span data-stu-id="7e49b-110">Strings</span></span>](index.md)
- [<span data-ttu-id="7e49b-111">建立新字串</span><span class="sxs-lookup"><span data-stu-id="7e49b-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="7e49b-112">操作字串</span><span class="sxs-lookup"><span data-stu-id="7e49b-112">Manipulating Strings</span></span>](../../../../standard/base-types/best-practices-strings.md)
