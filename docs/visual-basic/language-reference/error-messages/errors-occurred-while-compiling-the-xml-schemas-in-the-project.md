---
title: 編譯專案中的 XML 結構描述時發生錯誤
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 17c31301e28c757954e72ba103254f038905671f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874357"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="0c366-102">編譯專案中的 XML 結構描述時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="0c366-102">Errors occurred while compiling the XML schemas in the project</span></span>

<span data-ttu-id="0c366-103">編譯專案中的 XML 架構時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0c366-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="0c366-104">因此，無法使用 XML IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="0c366-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="0c366-105">專案中包含 (XSD) 架構的 XML 架構定義發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0c366-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="0c366-106">當您加入 XSD 架構 ( .xsd) 檔案，且該檔案與專案的現有 XSD 架構集發生衝突時，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="0c366-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="0c366-107">**錯誤識別碼：** BC36810</span><span class="sxs-lookup"><span data-stu-id="0c366-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0c366-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="0c366-108">To correct this error</span></span>  
  
- <span data-ttu-id="0c366-109">按兩下 [ **錯誤清單** ] 視窗中的警告。</span><span class="sxs-lookup"><span data-stu-id="0c366-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="0c366-110">Visual Basic 會帶您前往 XSD 檔案中的位置，這是警告的來源。</span><span class="sxs-lookup"><span data-stu-id="0c366-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="0c366-111">更正 XSD 架構中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0c366-111">Correct the error in the XSD schema.</span></span>  
  
- <span data-ttu-id="0c366-112">確定所有必要的 XSD 架構 ( .xsd) 檔案都包含在專案中。</span><span class="sxs-lookup"><span data-stu-id="0c366-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="0c366-113">您可能需要按一下 [**專案**] 功能表上的 [**顯示所有**檔案]，才能在**方案總管**中查看 .xsd 檔。</span><span class="sxs-lookup"><span data-stu-id="0c366-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="0c366-114">以滑鼠右鍵按一下 .xsd 檔案，然後按一下 [ **包含在專案中** ]，將檔案包含在您的專案中。</span><span class="sxs-lookup"><span data-stu-id="0c366-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
- <span data-ttu-id="0c366-115">如果您使用 XML to Schema Wizard，則如果您從相同的來源推斷出一次以上的架構，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="0c366-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="0c366-116">在此情況下，您可以從專案中移除現有的 XSD 架構檔案、將新的 XML 新增至架構專案範本，然後為 XML 提供適用于您專案的所有適用 XML 來源的 [XML 至架構]。</span><span class="sxs-lookup"><span data-stu-id="0c366-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
- <span data-ttu-id="0c366-117">如果 XSD 架構中找不到錯誤，XML 編譯器可能沒有足夠的資訊來提供詳細的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0c366-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="0c366-118">如果您確定專案中包含之 .xsd 檔的 XML 命名空間符合 Visual Studio 中設定之 XML 架構所識別的 XML 命名空間，您可能可以取得更詳細的錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="0c366-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c366-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c366-119">See also</span></span>

- [<span data-ttu-id="0c366-120">錯誤清單視窗</span><span class="sxs-lookup"><span data-stu-id="0c366-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)
- [<span data-ttu-id="0c366-121">XML</span><span class="sxs-lookup"><span data-stu-id="0c366-121">XML</span></span>](../../programming-guide/language-features/xml/index.md)
