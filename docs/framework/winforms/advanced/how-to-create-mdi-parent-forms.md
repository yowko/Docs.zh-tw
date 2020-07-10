---
title: 如何：建立 MDI 父表單
description: 瞭解如何以程式設計方式建立 MDI 父表單，以及如何使用 Windows Form 設計工具。
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: d387837a565ca247f62828c19f353990b35117c7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174701"
---
# <a name="how-to-create-mdi-parent-forms"></a>如何：建立 MDI 父表單

> [!IMPORTANT]
> 本主題使用 <xref:System.Windows.Forms.MainMenu> 控制項，該控制項已被 <xref:System.Windows.Forms.MenuStrip> 控制項取代。 您可以選擇保留 <xref:System.Windows.Forms.MainMenu> 控制項，以提供回溯相容性並供未來使用。 如需使用建立 MDI 父表單的詳細資訊 <xref:System.Windows.Forms.MenuStrip> ，請參閱[如何：使用 MENUSTRIP 建立 Mdi 視窗清單](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)。

MDI 父表單是多重文件介面 (MDI) 應用程式的基礎。 這個表單包含 MDI 子視窗，也就是使用者與 MDI 應用程式互動所在的子視窗。 您可以透過 Windows Form 設計工具及程式設計方式，輕鬆建立 MDI 父表單。

## <a name="create-an-mdi-parent-form-at-design-time"></a>在設計階段建立 MDI 父表單

1. 在 Visual Studio 中建立 Windows 應用程式專案。

2. 在 [**屬性**] 視窗中，將 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 [ **true**]。

     如此即可將表單指定為子視窗的 MDI 容器。

    > [!NOTE]
    > 當您設定 [屬性]**** 視窗中的屬性時，也可以視需要將 `WindowState` 屬性設定為 **Maximized**，這是因為當父表單最大化時，最容易操作 MDI 子視窗。 此外，請注意 MDI 父表單的邊緣會採用系統色彩 (在 Windows 系統控制台中設定)，而不是採用您使用 <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> 屬性所設定的背景色彩。

3. 從 [工具箱]**** 中，將 **MenuStrip** 控制項拖曳至表單。 建立一個最上層功能表項目，並將 **Text** 屬性設定為 **&File**，其中包含子功能表項目 **&New** 和 **&Close**。 另外再建立一個名為 **&Window** 的最上層功能表項目。

     第一個功能表會在執行階段建立及隱藏功能表項目，第二個功能表則會追蹤開啟的 MDI 子視窗。 此時，您已經建立 MDI 父視窗。

4. 按**F5**執行應用程式。 如需建立在 MDI 父表單內操作之 MDI 子視窗的資訊，請參閱[如何：建立 MDI 子表單](how-to-create-mdi-child-forms.md)。

## <a name="see-also"></a>另請參閱

- [多重文件介面 (MDI) 應用程式](multiple-document-interface-mdi-applications.md)
- [如何：建立 MDI 子表單](how-to-create-mdi-child-forms.md)
- [如何：決定作用中的 MDI 子系](how-to-determine-the-active-mdi-child.md)
- [如何：傳送資料至作用中的 MDI 子系](how-to-send-data-to-the-active-mdi-child.md)
- [如何：安排 MDI 子表單](how-to-arrange-mdi-child-forms.md)
