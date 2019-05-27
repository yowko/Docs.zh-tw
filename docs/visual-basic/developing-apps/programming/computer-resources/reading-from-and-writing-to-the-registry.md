---
title: 讀取和寫入登錄 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: fcc13d82a2b27221c13f9277585c21196b47003d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591473"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a>讀取和寫入登錄 (Visual Basic)
本主題描述與登錄建立關聯的工作和概念主題。  
  
 在 Visual Basic 中進行程式設計時，您可以選擇透過 Visual Basic 所提供的函式或是 .NET Framework 的登錄類別來存取登錄。 登錄會裝載作業系統的資訊，以及電腦所裝載的應用程式的資訊。 如果允許不適當地存取系統資源或受保護資訊，則使用登錄可能會危及安全性。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建立登錄機碼並設定其值](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 描述如何使用 `My.Computer.Registry` 物件的 `CreateSubKey` 和 `SetValue` 方法來建立登錄機碼，並設定其值。  
  
 [如何：讀取登錄機碼的值](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 描述如何使用 `My.Computer.Registry` 物件的 `GetValue` 方法來讀取登錄機碼中的值。  
  
 [如何：刪除登錄機碼](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 描述如何使用 `My.Computer.Registry.CurrentUser` 屬性的 `DeleteSubKey` 方法來刪除登錄機碼。  
  
 [使用 Microsoft.Win32 命名空間讀取和寫入登錄](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 描述如何使用 .NET Framework 的 `Registry` 和 `RegistryKey` 類別來存取登錄。  
  
 [安全性和登錄](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 討論與登錄有關的安全性問題。  
  
## <a name="related-sections"></a>相關章節  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 列出並說明 `My.Computer.Registry` 物件的成員。  
  
 <xref:Microsoft.Win32.Registry>  
 概述 `Registry` 類別，以及個別索引鍵和成員的連結。
