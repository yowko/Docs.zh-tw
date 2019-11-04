---
title: 如何：鎖定 Windows Form 的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d157ddc8be4b5fa0057241b562e76b566e8dad99
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458336"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>如何：鎖定控制項以 Windows Forms

當您設計 Windows 應用程式的使用者介面（UI）時，可以在控制項正確定位之後鎖定它們，以便在設定其他屬性時不會不慎移動或調整其大小。

此外，您可以一次鎖定和解除鎖定表單上的所有控制項，這對於具有許多控制項的表單很有説明，或者您也可以解除鎖定個別控制項。 當您將所有控制項放在表單上時，請將它們全部鎖定，以避免發生錯誤的移動。

## <a name="to-lock-a-control"></a>若要鎖定控制項

在 Visual Studio 的 [**屬性**] 視窗中，選取 [已**鎖定**] 屬性，然後選取 [ **true**]。 （按兩下名稱即可切換屬性設定）。

或者，以滑鼠右鍵按一下控制項，然後選擇 [**鎖定控制項**]。

> [!NOTE]
> 鎖定控制項可避免將它們拖曳至設計介面上的新大小或位置。 不過，您仍然可以透過 [**屬性**] 視窗或在程式碼中變更控制項的大小或位置。

## <a name="to-lock-all-the-controls-on-a-form"></a>鎖定表單上的所有控制項

從 [**格式**] 功能表選擇 [**鎖定控制項**]。

> [!NOTE]
> 此命令也會鎖定表單的大小，因為表單是控制項。

## <a name="to-unlock-all-locked-controls-on-a-form"></a>解除鎖定表單上所有鎖定的控制項

從 [**格式**] 功能表選擇 [**鎖定控制項**]。

表單上先前鎖定的所有控制項現在都會解除鎖定。

## <a name="to-unlock-locked-controls-individually"></a>個別解除鎖定鎖定的控制項

在 [**屬性**] 視窗中，選取 [已**鎖定**] 屬性，然後選取 [ **false**]。 （按兩下名稱即可切換屬性設定）。

## <a name="see-also"></a>請參閱

- [Windows Forms 控制項](index.md)
- [標記個別 Windows Forms 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Forms 控制項](windows-forms-controls-by-function.md)
