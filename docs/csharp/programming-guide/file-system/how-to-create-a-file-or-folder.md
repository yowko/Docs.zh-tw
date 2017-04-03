---
title: "如何：建立檔案或資料夾 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bba53c8d175d95aa3b89ba458517d439a8d2bb11
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>如何：建立檔案或資料夾 (C# 程式設計手冊)
您可以程式設計的方式在電腦上建立資料夾、建立子資料夾、在子資料夾中建立檔案，以及將資料寫入檔案。  
  
## <a name="example"></a>範例  
 [!code-cs[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-create-a-file-or-folder_1.cs)]  
  
 如果已有此資料夾，<xref:System.IO.Directory.CreateDirectory%2A> 不會執行任何動作，也不會擲回任何例外狀況。 不過，<xref:System.IO.File.Create%2A?displayProperty=fullName> 會使用新檔案取代現有的檔案。 此例使用 `if` - `else` 陳述式防止現有的檔案被取代。  
  
 透過在範例中進行下列變更，您可以根據是否已有具特定名稱的檔案來指定不同的結果。 如果沒有這類檔案，程式碼會建立一個。 如果有這類檔案，程式碼會將資料附加至該檔案。  
  
-   指定非隨機的檔案名稱。  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
  
    ```  
  
-   請在下列程式碼中以 `using` 陳述式取代 `if`-`else` 陳述式。  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
  
    ```  
  
 執行數次範例以確認資料是否每次都新增至檔案。  
  
 如需更多可以嘗試的 `FileMode` 值，請參 <xref:System.IO.FileMode>。  
  
 以下條件可能會造成例外狀況：  
  
-   資料夾名稱的格式不正確。 例如，它包含不合法的字元，或只有空白 (<xref:System.ArgumentException> 類別)。 使用 <xref:System.IO.Path> 類別建立有效的路徑名稱。  
  
-   要建立之資料夾的父資料夾是唯讀的 (<xref:System.IO.IOException> 類別)。  
  
-   資料夾名稱為 `null` (<xref:System.ArgumentNullException> 類別)。  
  
-   資料夾名稱太長 (<xref:System.IO.PathTooLongException> 類別)。  
  
-   資料夾名稱只有冒號 ":" (<xref:System.IO.PathTooLongException> 類別)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 部分信任情況下可能會擲回 <xref:System.Security.SecurityException> 類別的執行個體。  
  
 如果您沒有建立資料夾的權限，範例會擲回 <xref:System.UnauthorizedAccessException> 類別的執行個體。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO?displayProperty=fullName>   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [檔案系統和登錄 (C# 程式設計手冊)](../../../csharp/programming-guide/file-system/index.md)
