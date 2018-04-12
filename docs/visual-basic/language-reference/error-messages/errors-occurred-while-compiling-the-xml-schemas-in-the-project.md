---
title: 編譯專案中的 XML 結構描述時發生錯誤
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07233ed1c68f85878ffdd7131f64e30e158dc350
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="ecd31-102">編譯專案中的 XML 結構描述時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="ecd31-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="ecd31-103">編譯專案中的 XML 結構描述時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ecd31-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="ecd31-104">因為這個緣故，則無法使用 XML IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="ecd31-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="ecd31-105">在 XML 結構描述定義 (XSD) 結構描述中包含在專案中有錯誤。</span><span class="sxs-lookup"><span data-stu-id="ecd31-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="ecd31-106">當您將加入專案中設定與現有的 XSD 結構描述衝突的 XSD 結構描述 (.xsd) 檔案，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="ecd31-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="ecd31-107">**錯誤 ID:** BC36810</span><span class="sxs-lookup"><span data-stu-id="ecd31-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ecd31-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ecd31-108">To correct this error</span></span>  
  
-   <span data-ttu-id="ecd31-109">按兩下警告中的**錯誤清單**視窗。</span><span class="sxs-lookup"><span data-stu-id="ecd31-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="ecd31-110">Visual Basic 會帶您前往來源警告的 XSD 檔中的位置。</span><span class="sxs-lookup"><span data-stu-id="ecd31-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="ecd31-111">更正的 XSD 結構描述中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="ecd31-111">Correct the error in the XSD schema.</span></span>  
  
-   <span data-ttu-id="ecd31-112">請確定所有必要的 XSD 結構描述 (.xsd) 檔案會包含在專案中。</span><span class="sxs-lookup"><span data-stu-id="ecd31-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="ecd31-113">您可能需要按一下**顯示所有檔案**上**專案**中的檔案 功能表，查看您.xsd**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="ecd31-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="ecd31-114">以滑鼠右鍵按一下.xsd 檔案，然後按一下**包含在專案**以您的專案中包含的檔案。</span><span class="sxs-lookup"><span data-stu-id="ecd31-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
-   <span data-ttu-id="ecd31-115">如果您使用 XML to Schema 精靈時，如果您從相同來源推斷結構描述一次以上，就可以會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="ecd31-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="ecd31-116">在此情況下，您可以移除現有的 XSD 結構描述檔案從專案中，加入新的 XML 結構描述項目範本，然後再提供 XML to Schema 精靈與所有適用的 XML 來源專案。</span><span class="sxs-lookup"><span data-stu-id="ecd31-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
-   <span data-ttu-id="ecd31-117">如果在 XSD 結構描述中不發現任何錯誤，XML 編譯器可能沒有足夠的資訊來提供詳細的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="ecd31-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="ecd31-118">您可以取得更詳細的錯誤資訊，如果您確定.xsd 檔案的 XML 命名空間中包含您專案的相符項目識別為 Visual Studio 中設定的 XML 結構描述的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ecd31-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecd31-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecd31-119">See Also</span></span>  
 [<span data-ttu-id="ecd31-120">錯誤清單視窗</span><span class="sxs-lookup"><span data-stu-id="ecd31-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)  
 [<span data-ttu-id="ecd31-121">XML</span><span class="sxs-lookup"><span data-stu-id="ecd31-121">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
