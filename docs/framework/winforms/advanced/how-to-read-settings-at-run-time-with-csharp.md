---
title: 如何：在執行階段使用 C# 讀取設定
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 6a40718d57fad4041eeea2fded03b7256abbe8d1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710219"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>如何：在執行時間使用 C 讀取設定\#

您可以在執行階段透過屬性物件來讀取應用程式範圍和使用者範圍的設定。 Properties 物件會透過其定義所在之專案的預設命名空間中的屬性, 來公開專案的所有預設設定。  
  
## <a name="to-read-settings-at-run-time-with-c"></a>若要在執行時間使用 C 讀取設定\#
  
透過 Properties.Settings.Default 成員存取適當的設定。 下列範例示範如何指派名為 `myColor` 的設定給 BackColor 屬性。 它會要求您具有先前建立的設定檔，其中包含 `System.Drawing.Color` 類型之名為 `myColor` 的設定。 如需建立設定檔的相關資訊, [請參閱如何:在設計階段](how-to-create-a-new-setting-at-design-time.md)建立新的設定。  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>另請參閱

- [使用應用程式設定和使用者設定](using-application-settings-and-user-settings.md)
- [如何：在執行時間使用來寫入使用者設定C#](how-to-write-user-settings-at-run-time-with-csharp.md)
- [應用程式設定概觀](application-settings-overview.md)
