---
title: "如何：在 Visual Basic 中建立 XML 文件"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 63b6485de5aba2ca49d54a057045bec2062d12dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="d56ff-102">如何：在 Visual Basic 中建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="d56ff-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="d56ff-103">這個範例示範如何將 XML 文件註解加入至您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d56ff-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="d56ff-104">若要建立 XML 文件類型或成員</span><span class="sxs-lookup"><span data-stu-id="d56ff-104">To create XML documentation for a type or member</span></span>  
  
1.  <span data-ttu-id="d56ff-105">在**程式碼編輯器**，您的游標放在您要建立的文件類型或成員的上一行。</span><span class="sxs-lookup"><span data-stu-id="d56ff-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2.  <span data-ttu-id="d56ff-106">型別`'''`（三個單一-引號）。</span><span class="sxs-lookup"><span data-stu-id="d56ff-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="d56ff-107">型別或成員的 XML 基本架構就會加入**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="d56ff-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="d56ff-108">加入適當的標記之間的描述性資訊。</span><span class="sxs-lookup"><span data-stu-id="d56ff-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d56ff-109">如果您新增其他行的 XML 文件區塊內，每一行的開頭必須`'''`。</span><span class="sxs-lookup"><span data-stu-id="d56ff-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4.  <span data-ttu-id="d56ff-110">加入新的 XML 文件註解中使用的型別或成員的其他程式碼。</span><span class="sxs-lookup"><span data-stu-id="d56ff-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="d56ff-111">IntelliSense 會顯示從文字\<摘要 > 標記的型別或成員。</span><span class="sxs-lookup"><span data-stu-id="d56ff-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5.  <span data-ttu-id="d56ff-112">編譯程式碼來產生包含文件註解的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="d56ff-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="d56ff-113">如需詳細資訊，請參閱 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)。</span><span class="sxs-lookup"><span data-stu-id="d56ff-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d56ff-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d56ff-114">See Also</span></span>  
 [<span data-ttu-id="d56ff-115">使用 XML 加入程式碼註解</span><span class="sxs-lookup"><span data-stu-id="d56ff-115">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="d56ff-116">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="d56ff-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [<span data-ttu-id="d56ff-117">/doc</span><span class="sxs-lookup"><span data-stu-id="d56ff-117">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
