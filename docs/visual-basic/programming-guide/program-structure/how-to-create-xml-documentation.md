---
title: 如何：在 Visual Basic 中建立 XML 文件
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 3dfec94a3dd1b8da5d371529b91b47f018bb3843
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931808"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="a6f58-102">如何：在 Visual Basic 中建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="a6f58-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="a6f58-103">此範例示範如何將 XML 文件註解新增至您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a6f58-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="a6f58-104">若要建立的型別或成員的 XML 文件</span><span class="sxs-lookup"><span data-stu-id="a6f58-104">To create XML documentation for a type or member</span></span>  
  
1.  <span data-ttu-id="a6f58-105">在 **程式碼編輯器**，您的游標放在上面類型或成員的項目，您要建立文件行。</span><span class="sxs-lookup"><span data-stu-id="a6f58-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2.  <span data-ttu-id="a6f58-106">型別`'''`（三個單引號）。</span><span class="sxs-lookup"><span data-stu-id="a6f58-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="a6f58-107">型別或成員的 XML 基本架構中新增**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="a6f58-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="a6f58-108">新增適當的標記之間的描述性資訊。</span><span class="sxs-lookup"><span data-stu-id="a6f58-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6f58-109">如果您新增其他行，XML 文件區塊內，每一行的開頭必須`'''`。</span><span class="sxs-lookup"><span data-stu-id="a6f58-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4.  <span data-ttu-id="a6f58-110">新增額外的程式碼會使用新的 XML 文件註解中的型別或成員。</span><span class="sxs-lookup"><span data-stu-id="a6f58-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="a6f58-111">IntelliSense 會顯示從文字\<摘要 > 標記的型別或成員。</span><span class="sxs-lookup"><span data-stu-id="a6f58-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5.  <span data-ttu-id="a6f58-112">編譯程式碼以產生包含文件註解的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="a6f58-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="a6f58-113">如需詳細資訊，請參閱 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)。</span><span class="sxs-lookup"><span data-stu-id="a6f58-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f58-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6f58-114">See Also</span></span>  
 [<span data-ttu-id="a6f58-115">使用 XML 加入程式碼註解</span><span class="sxs-lookup"><span data-stu-id="a6f58-115">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="a6f58-116">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="a6f58-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)  
 [<span data-ttu-id="a6f58-117">/doc</span><span class="sxs-lookup"><span data-stu-id="a6f58-117">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
