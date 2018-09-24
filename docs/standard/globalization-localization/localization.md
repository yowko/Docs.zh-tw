---
title: 當地語系化
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee7de15130644e63b17a6d067c5cce9088d199a0
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46472139"
---
# <a name="localization"></a><span data-ttu-id="f7ea8-102">當地語系化</span><span class="sxs-lookup"><span data-stu-id="f7ea8-102">Localization</span></span>
<span data-ttu-id="f7ea8-103">當地語系化是一種程序，可將應用程式資源翻譯為應用程式所支援之每個文化特性的當地語系化版本。</span><span class="sxs-lookup"><span data-stu-id="f7ea8-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="f7ea8-104">只有在完成[可當地語系化檢閱](../../../docs/standard/globalization-localization/localizability-review.md)步驟，以確認全球化的應用程式已準備好進行當地語系化之後，才能繼續進行當地語系化步驟。</span><span class="sxs-lookup"><span data-stu-id="f7ea8-104">You should proceed to the localization step only after completing the [Localizability Review](../../../docs/standard/globalization-localization/localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>  
  
 <span data-ttu-id="f7ea8-105">準備好進行當地語系化的應用程式分成兩個概念性區塊，其中一個區塊包含所有使用者介面元素，另一個區塊則包含可執行檔程式碼。</span><span class="sxs-lookup"><span data-stu-id="f7ea8-105">An application that is ready for localization is separated into two conceptual blocks, a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="f7ea8-106">使用者介面區塊包含只可當地語系化的使用者介面元素，例如字串、錯誤訊息、對話方塊、功能表、內嵌物件資源，以及適用於中性文化特性的其他元素。</span><span class="sxs-lookup"><span data-stu-id="f7ea8-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="f7ea8-107">程式碼區塊僅包含可供所有支援的文化特性使用的應用程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="f7ea8-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="f7ea8-108">Common Language Runtime 支援附屬組件資源模型，可將應用程式的可執行檔程式碼與其資源分開。</span><span class="sxs-lookup"><span data-stu-id="f7ea8-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="f7ea8-109">如需有關實作此模組的詳細資訊，請參閱[桌面應用程式中的資源](../../../docs/framework/resources/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f7ea8-109">For more information about implementing this model, see [Resources in Desktop Apps](../../../docs/framework/resources/index.md).</span></span>  
  
 <span data-ttu-id="f7ea8-110">針對每個當地語系化版本的應用程式，加入新的附屬組件，其中包含轉譯成適用於目標文化特性之語言的當地語系化使用者介面區塊。</span><span class="sxs-lookup"><span data-stu-id="f7ea8-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="f7ea8-111">所有文化特性的程式碼區塊應該維持不變。</span><span class="sxs-lookup"><span data-stu-id="f7ea8-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="f7ea8-112">當地語系化版本的使用者介面區塊結合程式碼區塊之後，會產生您應用程式的當地語系化版本。</span><span class="sxs-lookup"><span data-stu-id="f7ea8-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>  
  
 <span data-ttu-id="f7ea8-113">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 提供的 Windows Forms 資源編輯器 (Winres.exe) 可讓您針對目標文化特性，快速當地語系化 Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="f7ea8-113">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="f7ea8-114">如需有關使用此工具的相關資訊，請參閱 [Winres.exe (Windows Forms 資源編輯器)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="f7ea8-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7ea8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7ea8-115">See also</span></span>

- [<span data-ttu-id="f7ea8-116">全球化和當地語系化</span><span class="sxs-lookup"><span data-stu-id="f7ea8-116">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
- [<span data-ttu-id="f7ea8-117">可當地語系化檢閱</span><span class="sxs-lookup"><span data-stu-id="f7ea8-117">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)  
- [<span data-ttu-id="f7ea8-118">全球化</span><span class="sxs-lookup"><span data-stu-id="f7ea8-118">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
- [<span data-ttu-id="f7ea8-119">桌面應用程式中的資源</span><span class="sxs-lookup"><span data-stu-id="f7ea8-119">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
