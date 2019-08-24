---
title: HOW TO：將 ActiveX 控制項新增至 Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 8c4c6c3f96c49401b032e360314794cc800c0551
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987068"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="4c7c8-102">作法：將 ActiveX 控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4c7c8-102">How to: Add ActiveX Controls to Windows Forms</span></span>

<span data-ttu-id="4c7c8-103">雖然 Visual Studio 中的 Windows Form 設計工具已經過優化, 可裝載 Windows Forms 控制項, 但您也可以將 ActiveX 控制項放在 Windows Forms 上。</span><span class="sxs-lookup"><span data-stu-id="4c7c8-103">While the Windows Forms Designer in Visual Studio is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>

> [!CAUTION]
> <span data-ttu-id="4c7c8-104">將 ActiveX 控制項加入至 Windows Forms 時, 會有效能限制。</span><span class="sxs-lookup"><span data-stu-id="4c7c8-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>

<span data-ttu-id="4c7c8-105">將 ActiveX 控制項新增至表單之前, 您必須先將其加入至 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="4c7c8-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="4c7c8-106">如需詳細資訊, 請參閱[COM 元件、自訂工具箱對話方塊](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="4c7c8-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span></span>

## <a name="add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="4c7c8-107">將 ActiveX 控制項新增至您的 Windows Form</span><span class="sxs-lookup"><span data-stu-id="4c7c8-107">Add an ActiveX control to your Windows Form</span></span>

<span data-ttu-id="4c7c8-108">若要將 ActiveX 控制項加入至 Windows Form, 請按兩下 [工具箱] 上的控制項。</span><span class="sxs-lookup"><span data-stu-id="4c7c8-108">To add an ActiveX control to your Windows Form, double-click the control on the Toolbox.</span></span>

<span data-ttu-id="4c7c8-109">Visual Studio 會將所有參考加入至專案中的控制項。</span><span class="sxs-lookup"><span data-stu-id="4c7c8-109">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="4c7c8-110">如需在 Windows Forms 上使用 ActiveX 控制項時應記住之事項的詳細資訊, 請參閱在[Windows Form 上裝載 Activex 控制項時的考慮](considerations-when-hosting-an-activex-control-on-a-windows-form.md)。</span><span class="sxs-lookup"><span data-stu-id="4c7c8-110">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4c7c8-111">在匯入 ActiveX 動態連結程式庫時, Windows Forms ActiveX 控制項匯入工具 (Aximp.exe) 會建立與預期不同類型的事件引數。</span><span class="sxs-lookup"><span data-stu-id="4c7c8-111">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="4c7c8-112">Aximp.exe 所建立的引數與下列類似: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, 需要時。 `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)`</span><span class="sxs-lookup"><span data-stu-id="4c7c8-112">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="4c7c8-113">請注意, 此 irregularity 不會防止程式碼正常運作。</span><span class="sxs-lookup"><span data-stu-id="4c7c8-113">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="4c7c8-114">如需詳細資訊, 請參閱[Windows Forms ActiveX 控制項匯入工具 (aximp.exe .exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md)。</span><span class="sxs-lookup"><span data-stu-id="4c7c8-114">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c7c8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c7c8-115">See also</span></span>

- [<span data-ttu-id="4c7c8-116">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="4c7c8-116">Windows Forms Controls</span></span>](index.md)
- <span data-ttu-id="4c7c8-117">[比較各種語言和程式庫的控制項與可以透過程式設計的物件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4c7c8-117">[Controls and Programmable Objects Compared in Various Languages and Libraries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span></span>
- [<span data-ttu-id="4c7c8-118">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4c7c8-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="4c7c8-119">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="4c7c8-119">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="4c7c8-120">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="4c7c8-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="4c7c8-121">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="4c7c8-121">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
