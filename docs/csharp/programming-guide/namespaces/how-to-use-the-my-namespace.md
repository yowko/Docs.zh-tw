---
title: "如何：使用 My 命名空間 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, My 命名空間存取"
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# 如何：使用 My 命名空間 (C# 程式設計手冊)
<xref:Microsoft.VisualBasic.MyServices> 命名空間 \(`My`\) 提供簡單而直覺的存取方式，可讓您存取各種 .NET Framework 類別，並撰寫與電腦、應用程式、設定、資源等互動的程式碼。  雖然 `MyServices` 命名空間原本是設計來搭配 Visual Basic 使用，不過您也可以在 C\# 應用程式中使用這個命名空間。  
  
 如需從 Visual Basic 使用 `MyServices` 命名空間的詳細資訊，請參閱[Development with My](../../../visual-basic/developing-apps/development-with-my/index.md)。  
  
## 加入參考  
 在方案中使用 `MyServices` 類別之前，您必須先加入對 Visual Basic 程式庫的參考。  
  
#### 若要加入對 Visual Basic 程式庫的參考  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**參考**\] 節點，然後選取 \[**加入參考**\]。  
  
2.  當 \[**參考**\] 對話方塊出現時，向下捲動清單並選取 Microsoft.VisualBasic.dll。  
  
     您可能也要在程式開頭的 `using` 段落中加入下列這行。  
  
     [!code-cs[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces3.cs#18)]  
  
## 範例  
 這個範例會呼叫 `MyServices` 命名空間中包含的各種靜態方法。  若要編譯這段程式碼，必須將對 Microsoft.VisualBasic.DLL 的參考加入至專案中。  
  
 [!code-cs[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces3.cs#19)]  
  
 C\# 應用程式不一定能夠呼叫 `MyServices` 命名空間中的所有類別，例如 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> 類別就不相容。  在這個特殊情況中，可以改用屬於 <xref:Microsoft.VisualBasic.FileIO.FileSystem> \(也包含在 VisualBasic.dll 檔案中\) 的靜態方法。  例如，下面便示範如何使用這類方法複製目錄：  
  
 [!code-cs[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces3.cs#20)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [命名空間](../../../csharp/programming-guide/namespaces/index.md)   
 [使用命名空間](../../../csharp/programming-guide/namespaces/using-namespaces.md)