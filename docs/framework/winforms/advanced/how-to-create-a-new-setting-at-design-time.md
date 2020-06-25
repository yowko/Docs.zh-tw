---
title: 如何：在設計階段建立新設定
description: 瞭解如何使用 Visual Studio 中的 [設定設計工具]，在設計階段建立新的 Windows Forms 設定。
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: ce37b42191999e29de2f2f7f7e7abfa0ec3f4d47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325844"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a>如何：在設計階段建立新設定

您可以在設計階段使用 Visual Studio 中的 [設定設計工具] 來建立新的設定。 [設定設計工具] 是格線樣式的介面，可讓您建立新的設定，並指定這些設定的屬性。 您必須為新的設定指定 [名稱]、[值]、[類型] 和 [範圍]。 一旦建立設定之後，就可以在程式碼中存取它。

## <a name="create-a-new-setting-at-design-time-in-c"></a>在設計階段于 C 中建立新的設定\#

1. 開啟 Visual Studio。

2. 在**方案總管**中，展開專案的 [**屬性**] 節點。

3. 按兩下要在其中新增設定的設定檔案。 這個檔案的預設名稱是 [設定]。

4. 在 [設定設計工具] 中，設定您設定的**名稱**、**值**、**類型**和**範圍**。 每個資料列都代表一個設定。

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a>在設計階段于 Visual Basic 中建立新的設定

1. 開啟 Visual Studio。

2. 在**方案總管**中，以滑鼠右鍵按一下您的專案節點，然後選擇 [**屬性**]。

3. 在 [**屬性**] 頁面中，選取 [**設定**] 索引標籤。

4. 在 [設定設計工具] 中，設定您設定的**名稱**、**值**、**類型**和**範圍**。 每個資料列都代表一個設定。

## <a name="see-also"></a>另請參閱

- [使用應用程式設定和使用者設定](using-application-settings-and-user-settings.md)
- [應用程式設定總覽](application-settings-overview.md)
- [如何：在設計階段變更現有設定的值](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
