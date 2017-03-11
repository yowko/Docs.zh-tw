---
title: "如何：建立檔案或資料夾 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "建立檔案 [C#]"
  - "建立資料夾 [C#]"
  - "檔案 [C#]"
  - "資料夾 [C#]"
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# 如何：建立檔案或資料夾 (C# 程式設計手冊)
您可以用程式設計方式在電腦上建立資料夾、建立子資料夾、在子資料夾中建立檔案，並在檔案中寫入資料。  
  
## 範例  
 [!code-cs[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/csharp/csFilesFolders/FileIteration.cs#10)]  
  
 如果資料夾已存在，<xref:System.IO.Directory.CreateDirectory%2A> 不會執行任何動作，也不會擲回例外狀況。  不過，<xref:System.IO.File.Create%2A?displayProperty=fullName> 會將現有檔案取代為新檔案。  範例會使用 `if`\-`else` 陳述式，防止現有檔案被取代。  
  
 藉由進行範例中的下列變更，您可以根據有特定名稱的檔案是否存在來指定不同的結果。  如果這類檔案不存在，則程式碼會建立該檔案。  如果這類檔案存在，則程式碼會附加資料至該檔案。  
  
-   指定非隨機檔案名稱。  
  
    ```c#  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
  
    ```  
  
-   以下列程式碼中的 `using` 陳述式取代 `if`\-`else` 陳述式。  
  
    ```c#  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
  
    ```  
  
 執行範例數次以驗證資料每次都會加入至檔案。  
  
 如需更多可以嘗試的 `FileMode` 值，請參閱 <xref:System.IO.FileMode>。  
  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   資料夾名稱錯誤。  例如，它包含不合法的字元或者它只是泛空白字元 \(White Space\) \(<xref:System.ArgumentException> 類別\)。  使用 <xref:System.IO.Path> 類別建立有效的路徑名稱。  
  
-   所要建立的資料夾的父資料夾是唯讀的 \(<xref:System.IO.IOException> 類別\)。  
  
-   資料夾名稱是 `null` \(<xref:System.ArgumentNullException> 類別\)。  
  
-   資料夾名稱太長 \(<xref:System.IO.PathTooLongException> 類別\)。  
  
-   資料夾名稱只是冒號 ":" \(<xref:System.IO.PathTooLongException> 類別\)。  
  
## .NET Framework 安全性  
 在部分信任的情況下可能會擲回 <xref:System.Security.SecurityException> 類別的執行個體。  
  
 如果您不具有建立資料夾的權限，這個範例將會擲回 <xref:System.UnauthorizedAccessException> 類別的執行個體。  
  
## 請參閱  
 <xref:System.IO?displayProperty=fullName>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [檔案系統和登錄](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)