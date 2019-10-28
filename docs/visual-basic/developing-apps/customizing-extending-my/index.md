---
title: 使用 Visual Basic 自訂專案和擴充 My 物件
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 06ca80b9-1192-4eb5-8537-8ef5edfb9be0
ms.openlocfilehash: 97933a9d014a54d5b6e333090cddccace99fcc3c
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2019
ms.locfileid: "72960949"
---
# <a name="customizing-projects-and-extending-my-with-visual-basic"></a><span data-ttu-id="fcdc9-102">使用 Visual Basic 自訂專案和擴充 My 物件</span><span class="sxs-lookup"><span data-stu-id="fcdc9-102">Customizing Projects and Extending My with Visual Basic</span></span>

<span data-ttu-id="fcdc9-103">您可以自訂專案範本，以提供額外的 `My` 物件。</span><span class="sxs-lookup"><span data-stu-id="fcdc9-103">You can customize project templates to provide additional `My` objects.</span></span> <span data-ttu-id="fcdc9-104">這可讓其他開發人員輕鬆地尋找和使用您的物件。</span><span class="sxs-lookup"><span data-stu-id="fcdc9-104">This makes it easy for other developers to find and use your objects.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fcdc9-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="fcdc9-105">In this section</span></span>

- [<span data-ttu-id="fcdc9-106">擴充 Visual Basic 中的 My 命名空間</span><span class="sxs-lookup"><span data-stu-id="fcdc9-106">Extending the My Namespace in Visual Basic</span></span>](extending-the-my-namespace.md)  
 <span data-ttu-id="fcdc9-107">描述如何將自訂成員和值新增至 Visual Basic 中的 `My` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="fcdc9-107">Describes how to add custom members and values to the `My` namespace in Visual Basic.</span></span>
- [<span data-ttu-id="fcdc9-108">封裝和部署自訂的 My 擴充</span><span class="sxs-lookup"><span data-stu-id="fcdc9-108">Packaging and Deploying Custom My Extensions</span></span>](packaging-and-deploying-custom-my-extensions.md)  
 <span data-ttu-id="fcdc9-109">描述如何使用 Visual Studio 範本發行自訂 `My` 命名空間延伸模組。</span><span class="sxs-lookup"><span data-stu-id="fcdc9-109">Describes how to publish custom `My` namespace extensions by using Visual Studio templates.</span></span>
- [<span data-ttu-id="fcdc9-110">擴充 Visual Basic 應用程式模型</span><span class="sxs-lookup"><span data-stu-id="fcdc9-110">Extending the Visual Basic Application Model</span></span>](extending-the-visual-basic-application-model.md)  
 <span data-ttu-id="fcdc9-111">描述如何藉由覆寫 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> 類別的成員，來指定您自己的應用程式模型延伸模組。</span><span class="sxs-lookup"><span data-stu-id="fcdc9-111">Describes how to specify your own extensions to the application model by overriding members of the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class.</span></span>
- [<span data-ttu-id="fcdc9-112">自訂 My 中可用的物件</span><span class="sxs-lookup"><span data-stu-id="fcdc9-112">Customizing Which Objects are Available in My</span></span>](customizing-which-objects-are-available-in-my.md)  
 <span data-ttu-id="fcdc9-113">描述如何設定專案的 \_MYTYPE 條件式編譯常數，以控制要啟用哪些 `My` 物件。</span><span class="sxs-lookup"><span data-stu-id="fcdc9-113">Describes how to control which `My` objects are enabled by setting your project's \_MYTYPE conditional-compilation constant.</span></span>

## <a name="related-sections"></a><span data-ttu-id="fcdc9-114">相關章節</span><span class="sxs-lookup"><span data-stu-id="fcdc9-114">Related sections</span></span>

- [<span data-ttu-id="fcdc9-115">使用 My 進行開發</span><span class="sxs-lookup"><span data-stu-id="fcdc9-115">Development with My</span></span>](../development-with-my/index.md)  
 <span data-ttu-id="fcdc9-116">描述預設會在不同的專案類型中提供哪些 `My` 物件。</span><span class="sxs-lookup"><span data-stu-id="fcdc9-116">Describes which `My` objects are available in different project types by default.</span></span>
- [<span data-ttu-id="fcdc9-117">Visual Basic 應用程式模型概觀</span><span class="sxs-lookup"><span data-stu-id="fcdc9-117">Overview of the Visual Basic Application Model</span></span>](../development-with-my/overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="fcdc9-118">描述 Visual Basic 的模型，以控制 Windows Forms 應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="fcdc9-118">Describes Visual Basic's model for controlling the behavior of Windows Forms applications.</span></span>
- [<span data-ttu-id="fcdc9-119">My 如何相依於專案類型</span><span class="sxs-lookup"><span data-stu-id="fcdc9-119">How My Depends on Project Type</span></span>](../development-with-my/how-my-depends-on-project-type.md)  
 <span data-ttu-id="fcdc9-120">描述預設會在不同的專案類型中提供哪些 `My` 物件。</span><span class="sxs-lookup"><span data-stu-id="fcdc9-120">Describes which `My` objects are available in different project types by default.</span></span>
- [<span data-ttu-id="fcdc9-121">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="fcdc9-121">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="fcdc9-122">討論編譯器如何使用條件式編譯來選取特定的程式碼區段，以編譯和排除其他區段。</span><span class="sxs-lookup"><span data-stu-id="fcdc9-122">Discusses how the compiler uses conditional-compilation to select particular sections of code to compile and exclude other sections.</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <span data-ttu-id="fcdc9-123">描述提供與目前應用程式相關之屬性、方法和事件的 `My` 物件。</span><span class="sxs-lookup"><span data-stu-id="fcdc9-123">Describes the `My` object that provides properties, methods, and events related to the current application.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcdc9-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="fcdc9-124">See also</span></span>

- [<span data-ttu-id="fcdc9-125">使用 Visual Basic 開發應用程式</span><span class="sxs-lookup"><span data-stu-id="fcdc9-125">Developing Applications with Visual Basic</span></span>](../index.md)
