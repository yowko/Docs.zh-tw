---
title: "如何︰ 在 Visual Basic 中建立 XML 文件 |Microsoft 文件"
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
- XML comments
- XML documentation, creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: 17
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 3171877f4fa1913b5535d71d671cea97b5a22850
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="56aac-102">如何：在 Visual Basic 中建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="56aac-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="56aac-103">這個範例示範如何將 XML 文件註解加入至您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="56aac-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="56aac-104">若要建立 XML 文件類型或成員</span><span class="sxs-lookup"><span data-stu-id="56aac-104">To create XML documentation for a type or member</span></span>  
  
1.  <span data-ttu-id="56aac-105">在**程式碼編輯器**，將游標位置的上一行類型或成員的項目，您要建立文件。</span><span class="sxs-lookup"><span data-stu-id="56aac-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2.  <span data-ttu-id="56aac-106">型別`'''`（三個單引號）。</span><span class="sxs-lookup"><span data-stu-id="56aac-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="56aac-107">型別或成員的 XML 基本架構中加入**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="56aac-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="56aac-108">新增適當的標記之間的描述性資訊。</span><span class="sxs-lookup"><span data-stu-id="56aac-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56aac-109">如果您新增其他行的 XML 文件區塊內，每一行開頭必須`'''`。</span><span class="sxs-lookup"><span data-stu-id="56aac-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4.  <span data-ttu-id="56aac-110">新增額外的程式碼會使用新的 XML 文件註解的型別或成員。</span><span class="sxs-lookup"><span data-stu-id="56aac-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="56aac-111">IntelliSense 中顯示的文字\<摘要 > 標記的型別或成員。</span><span class="sxs-lookup"><span data-stu-id="56aac-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5.  <span data-ttu-id="56aac-112">編譯程式碼以產生包含文件註解的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="56aac-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="56aac-113">如需詳細資訊，請參閱[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)。</span><span class="sxs-lookup"><span data-stu-id="56aac-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56aac-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56aac-114">See Also</span></span>  
 <span data-ttu-id="56aac-115">[記錄與 XML 程式碼](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span><span class="sxs-lookup"><span data-stu-id="56aac-115">[Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span></span>  
<span data-ttu-id="56aac-116"> [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span><span class="sxs-lookup"><span data-stu-id="56aac-116"> [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span></span>  
<span data-ttu-id="56aac-117"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)</span><span class="sxs-lookup"><span data-stu-id="56aac-117"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)</span></span>
