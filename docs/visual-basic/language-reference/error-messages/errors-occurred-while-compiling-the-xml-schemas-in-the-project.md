---
title: 編譯專案中的 XML 結構描述時發生錯誤
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 337fc1fb4dfc83c9b4814d3e45eb0cbe0758f7ce
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842521"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="1bf9a-102">編譯專案中的 XML 結構描述時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="1bf9a-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="1bf9a-103">編譯專案中的 XML 結構描述時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bf9a-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="1bf9a-104">因為這個緣故，XML IntelliSense 無法使用。</span><span class="sxs-lookup"><span data-stu-id="1bf9a-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="1bf9a-105">在專案中包含的 XML 結構描述定義 (XSD) 結構描述中沒有錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bf9a-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="1bf9a-106">當您將加入專案中設定與現有的 XSD 結構描述衝突的 XSD 結構描述 (.xsd) 檔案，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bf9a-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="1bf9a-107">**錯誤 ID:** BC36810</span><span class="sxs-lookup"><span data-stu-id="1bf9a-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1bf9a-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1bf9a-108">To correct this error</span></span>  
  
-   <span data-ttu-id="1bf9a-109">按兩下警告**錯誤清單**視窗。</span><span class="sxs-lookup"><span data-stu-id="1bf9a-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="1bf9a-110">Visual Basic 會帶您前往中做為來源的警告與 XSD 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="1bf9a-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="1bf9a-111">更正的 XSD 結構描述中的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="1bf9a-111">Correct the error in the XSD schema.</span></span>  
  
-   <span data-ttu-id="1bf9a-112">請確定所有必要的 XSD 結構描述 (.xsd) 檔案包含在專案中。</span><span class="sxs-lookup"><span data-stu-id="1bf9a-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="1bf9a-113">您可能需要按一下**顯示所有檔案**上**專案**中的功能表以查看您的.xsd 檔案**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="1bf9a-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="1bf9a-114">以滑鼠右鍵按一下 .xsd 檔案，然後按一下**加入至專案**以在您的專案中包含的檔案。</span><span class="sxs-lookup"><span data-stu-id="1bf9a-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
-   <span data-ttu-id="1bf9a-115">如果您使用 XML to Schema 精靈時，如果您從相同來源推斷結構描述一次以上，就可以會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bf9a-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="1bf9a-116">在此情況下，您可以從專案中，移除現有的 XSD 結構描述檔案加入新的 XML 結構描述項目範本，然後再提供 XML to Schema 精靈與所有適用的 XML 來源專案。</span><span class="sxs-lookup"><span data-stu-id="1bf9a-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
-   <span data-ttu-id="1bf9a-117">如果您的 XSD 結構描述中任何錯誤，XML 編譯器可能沒有足夠的資訊來提供詳細的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="1bf9a-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="1bf9a-118">您可以取得更詳細的錯誤資訊，如果您確定為.xsd 檔的 XML 命名空間包含您專案的相符項目中所識別的 Visual Studio 中設定的 XML 結構描述的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="1bf9a-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf9a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bf9a-119">See also</span></span>

- [<span data-ttu-id="1bf9a-120">錯誤清單視窗</span><span class="sxs-lookup"><span data-stu-id="1bf9a-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)
- [<span data-ttu-id="1bf9a-121">XML</span><span class="sxs-lookup"><span data-stu-id="1bf9a-121">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
