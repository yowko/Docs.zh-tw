---
title: 如何：在執行階段使用 C# 讀取設定
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8cdc1a79f1ab327ae037cd6a04aa769196405127
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966901"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>如何：在執行階段使用 c# 讀取設定\#

您可以在執行階段透過屬性物件來讀取應用程式範圍和使用者範圍的設定。 屬性物件會透過 Properties.Settings.Default 成員公開所有專案的預設值。  
  
## <a name="to-read-settings-at-run-time-with-c"></a>若要在執行階段使用 c# 讀取設定\#
  
透過 Properties.Settings.Default 成員存取適當的設定。 下列範例示範如何指派名為 `myColor` 的設定給 BackColor 屬性。 它會要求您具有先前建立的設定檔，其中包含 `System.Drawing.Color` 類型之名為 `myColor` 的設定。 如需建立設定檔資訊，請參閱[How To:在設計階段建立新的設定](how-to-create-a-new-setting-at-design-time.md)。  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>另請參閱

- [使用應用程式設定和使用者設定](using-application-settings-and-user-settings.md)
- [如何：在執行階段撰寫使用者設定C#](how-to-write-user-settings-at-run-time-with-csharp.md)
- [應用程式設定概觀](application-settings-overview.md)
