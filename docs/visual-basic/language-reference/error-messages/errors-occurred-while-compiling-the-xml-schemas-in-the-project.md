---
title: "編譯專案中的 XML 結構描述時發生錯誤 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36810
- vbc36810
dev_langs:
- VB
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: 11
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
ms.openlocfilehash: 7e6a835f84f2e37f4f583bc16c24cf9bb28cc92a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="4c127-102">編譯專案中的 XML 結構描述時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="4c127-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="4c127-103">編譯專案中的 XML 結構描述時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4c127-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="4c127-104">因為這個緣故，XML IntelliSense 無法使用。</span><span class="sxs-lookup"><span data-stu-id="4c127-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="4c127-105">包含在專案中的 XML 結構描述定義 (XSD) 結構描述中沒有錯誤。</span><span class="sxs-lookup"><span data-stu-id="4c127-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="4c127-106">當您將加入專案中設定與現有的 XSD 結構描述衝突的 XSD 結構描述 (.xsd) 檔案，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="4c127-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="4c127-107">**錯誤識別碼︰** BC36810</span><span class="sxs-lookup"><span data-stu-id="4c127-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4c127-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4c127-108">To correct this error</span></span>  
  
-   <span data-ttu-id="4c127-109">按兩下警告中的**錯誤清單**視窗。</span><span class="sxs-lookup"><span data-stu-id="4c127-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="4c127-110">Visual Basic 會帶您前往來源警告的 XSD 檔中的位置。</span><span class="sxs-lookup"><span data-stu-id="4c127-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="4c127-111">更正 XSD 結構描述中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4c127-111">Correct the error in the XSD schema.</span></span>  
  
-   <span data-ttu-id="4c127-112">請確定所有必要的 XSD 結構描述 (.xsd) 檔案包含在專案中。</span><span class="sxs-lookup"><span data-stu-id="4c127-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="4c127-113">您可能需要按一下**顯示所有檔案**上**專案**中的檔案 功能表上，若要查看您.xsd**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="4c127-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="4c127-114">以滑鼠右鍵按一下.xsd 檔案，然後按一下**加入至專案**將檔案併入專案中。</span><span class="sxs-lookup"><span data-stu-id="4c127-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
-   <span data-ttu-id="4c127-115">如果您使用 XML to Schema 精靈時，如果您從相同來源推斷結構描述一次以上，就可以會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="4c127-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="4c127-116">在此情況下，您可以從專案移除現有的 XSD 結構描述檔案加入新的 XML 結構描述項目範本，然後再提供 XML 結構描述精靈與所有適用的 XML 來源專案。</span><span class="sxs-lookup"><span data-stu-id="4c127-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
-   <span data-ttu-id="4c127-117">如果您的 XSD 結構描述中沒有識別任何錯誤，XML 編譯器可能沒有足夠的資訊來提供詳細的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="4c127-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="4c127-118">您可以取得更詳細的錯誤資訊，如果您確定為.xsd 檔的 XML 命名空間包含在專案的比對識別 Visual Studio 中設定的 XML 結構描述的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="4c127-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c127-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c127-119">See Also</span></span>  
 <span data-ttu-id="4c127-120">[錯誤清單視窗](https://docs.microsoft.com/visualstudio/ide/reference/error-list-window) </span><span class="sxs-lookup"><span data-stu-id="4c127-120">[Error List Window](https://docs.microsoft.com/visualstudio/ide/reference/error-list-window) </span></span>  
<span data-ttu-id="4c127-121"> [在 Visual Basic 中的 XML IntelliSense](../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md) </span><span class="sxs-lookup"><span data-stu-id="4c127-121"> [XML IntelliSense in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md) </span></span>  
<span data-ttu-id="4c127-122"> [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)</span><span class="sxs-lookup"><span data-stu-id="4c127-122"> [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)</span></span>
