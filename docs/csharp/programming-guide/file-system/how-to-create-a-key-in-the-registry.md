---
title: "如何：在登錄中建立機碼 (Visual C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6cc79a8a914d3ef5b7c496db4dc0d2b3eb17768
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a>如何：在登錄中建立機碼 (Visual C#)
本範例會將 "Name" 和 "Isabella" 的值組新增至目前使用者之登錄的 "Names" 索引鍵下。  
  
## <a name="example"></a>範例  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   將程式碼複製並貼入主控台應用程式的 `Main` 方法中。  
  
-   以直接位在登錄的 HKEY_CURRENT_USER 節點下的索引鍵名稱取代 `Names` 參數。  
  
-   以直接位在 Names 節點下的值名稱取代 `Name` 參數。  
  
## <a name="robust-programming"></a>穩固程式設計  
 檢查登錄結構以找出適合索引鍵的位置。 例如，您可能想要開啟目前使用者的軟體金鑰，並以貴公司的名稱建立金鑰。 請將登錄值新增至貴公司的索引鍵。  
  
 以下條件可能會造成例外狀況：  
  
-   索引鍵名稱是 Null。  
  
-   使用者沒有權限，無法建立登錄機碼。  
  
-   索引鍵名稱超過 255 個字元的限制。  
  
-   機碼已關閉。  
  
-   登錄機碼為唯讀。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 將資料寫入使用者資料夾 `Microsoft.Win32.Registry.CurrentUser` 比寫入本機電腦 `Microsoft.Win32.Registry.LocalMachine` 更安全。  
  
 當您建立登錄值時，您需要決定如果該值已經存在該怎麼辦。 另一個可能是惡意的處理序，可能已建立值並具有其存取權。 當您將資料放在登錄值中時，資料可供其他處理序使用。 為避免此問題，請使用 `Overload:Microsoft.Win32.RegistryKey.GetValue`。 方法。 如果沒有索引鍵，則傳回 Null。  
  
 即使使用存取控制清單 (ACL) 來保護登錄機碼，將密碼等機密資料以純文字儲存在登錄中也不安全。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO?displayProperty=nameWithType>  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [檔案系統和登錄 (C# 程式設計指南)](../../../csharp/programming-guide/file-system/index.md)  
 [使用 C# 從登錄進行讀取、寫入和刪除](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
