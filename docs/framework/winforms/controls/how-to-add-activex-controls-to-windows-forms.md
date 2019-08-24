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
# <a name="how-to-add-activex-controls-to-windows-forms"></a>作法：將 ActiveX 控制項新增至 Windows Forms

雖然 Visual Studio 中的 Windows Form 設計工具已經過優化, 可裝載 Windows Forms 控制項, 但您也可以將 ActiveX 控制項放在 Windows Forms 上。

> [!CAUTION]
> 將 ActiveX 控制項加入至 Windows Forms 時, 會有效能限制。

將 ActiveX 控制項新增至表單之前, 您必須先將其加入至 [工具箱]。 如需詳細資訊, 請參閱[COM 元件、自訂工具箱對話方塊](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100))。

## <a name="add-an-activex-control-to-your-windows-form"></a>將 ActiveX 控制項新增至您的 Windows Form

若要將 ActiveX 控制項加入至 Windows Form, 請按兩下 [工具箱] 上的控制項。

Visual Studio 會將所有參考加入至專案中的控制項。 如需在 Windows Forms 上使用 ActiveX 控制項時應記住之事項的詳細資訊, 請參閱在[Windows Form 上裝載 Activex 控制項時的考慮](considerations-when-hosting-an-activex-control-on-a-windows-form.md)。

> [!NOTE]
> 在匯入 ActiveX 動態連結程式庫時, Windows Forms ActiveX 控制項匯入工具 (Aximp.exe) 會建立與預期不同類型的事件引數。 Aximp.exe 所建立的引數與下列類似: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, 需要時。 `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` 請注意, 此 irregularity 不會防止程式碼正常運作。 如需詳細資訊, 請參閱[Windows Forms ActiveX 控制項匯入工具 (aximp.exe .exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md)。

## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項](index.md)
- [比較各種語言和程式庫的控制項與可以透過程式設計的物件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
- [標記個別 Windows Forms 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Forms 控制項](windows-forms-controls-by-function.md)
