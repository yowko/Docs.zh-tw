---
title: HOW TO：將 ActiveX 控制項新增至 Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 17311adade187ef3c8e4e639299e6c5cbbcd98a9
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210384"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>HOW TO：將 ActiveX 控制項新增至 Windows Forms

雖然 Visual Studio 中的 Windows Form 設計工具已最佳化來裝載 Windows Forms 控制項中，您也可以使 Windows Form 上的 ActiveX 控制項。

> [!CAUTION]
> ActiveX 控制項新增至它們時，則需要有 Windows Forms 的效能限制。

您將 ActiveX 控制項新增至您的表單之前，您必須將它們加入 [工具箱] 中。 如需詳細資訊，請參閱 < [COM 元件、 自訂工具箱對話方塊](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100))。

## <a name="add-an-activex-control-to-your-windows-form"></a>將 ActiveX 控制項新增至您的 Windows 表單

若要加入 Windows Form ActiveX 控制項，連按兩下 [工具箱] 上的控制項。

Visual Studio 專案中新增至控制項的所有參考。 如需有關使用 Windows Form 上的 ActiveX 控制項時，請記住的事項的詳細資訊，請參閱[裝載在 Windows Form 上的 ActiveX 控制項的考慮因素](considerations-when-hosting-an-activex-control-on-a-windows-form.md)。

> [!NOTE]
> 非預期的 ActiveX 動態連結程式庫匯入作業時，Windows Forms ActiveX 控制項匯入工具 (AxImp.exe) 就會建立不同類型的事件引數。 AxImp.exe 所建立的引數會與下列類似： `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`，當`Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)`預期。 請注意，此種不規則變化不會防止程式碼正常運作。 如需詳細資訊，請參閱 < [Windows Forms ActiveX 控制項匯入工具 (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md)。

## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項](index.md)
- [比較各種語言和程式庫的控制項與可以透過程式設計的物件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
- [排列 Windows Forms 上的控制項](arranging-controls-on-windows-forms.md)
- [標記個別 Windows Forms 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Forms 控制項](windows-forms-controls-by-function.md)
