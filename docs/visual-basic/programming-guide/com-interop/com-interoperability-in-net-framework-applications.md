---
title: "COM Interoperability in .NET Framework Applications (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "interoperability, COM and .NET framework objects"
  - "COM interop"
  - "shared components"
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# COM Interoperability in .NET Framework Applications (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

要在同一應用程式中使用 COM 物件和 .NET Framework 物件時，您需要解決物件在記憶體中以不同方式存在的問題。  .NET Framework 物件位於 Managed 記憶體 \(也就是由 Common Language Runtime 控制的記憶體\) 中，而且執行階段可視需要將其加以移動。  COM 物件則位於 Unmanaged 記憶體中，不會移到其他記憶體位置。  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 和 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 提供了工具，可讓您控制這些 Managed 和 Unmanaged 元件之間的互動。  如需 Managed 程式碼的詳細資訊，請參閱 [Common Language Runtime](../Topic/Common%20Language%20Runtime%20\(CLR\).md)。  
  
 除了在 .NET 應用程式中使用 COM 物件外，您也可能想使用 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)]，開發可透過 COM，從 Unmanaged 程式碼中存取的物件。  
  
 這個頁面上的連結提供 COM 與 .NET Framework 物件之間的詳細互動資料。  
  
## 相關章節  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 提供涵蓋 Visual Basic 的 COM 互通性 \(Interoperability\) 主題的連結，包括 COM 物件、ActiveX 控制項、Win32 DLL、Managed 物件和 COM 物件的繼承 \(Inheritance\)。  
  
 [COM Interop Wrapper Error](/visual-cpp/misc/com-interop-wrapper-error)  
 說明如果專案系統無法為特定元件建立 COM 互通性包裝函式時的後果和選項。  
  
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)  
 簡要說明 Managed 和 Unmanaged 程式碼間互動的一些問題，並且提供詳細資訊的連結。  
  
 [COM 包裝函式](../Topic/COM%20Wrappers.md)  
 討論允許 Managed 程式碼呼叫 COM 方法的執行階段可呼叫包裝函式，以及允許 COM 用戶端呼叫 .NET 物件方法的 COM 可呼叫包裝函式。  
  
 [Advanced COM Interoperability](http://msdn.microsoft.com/zh-tw/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 提供主題的連結，涵蓋 COM 互通性的包裝函式、例外狀況 \(Exception\)、繼承、執行緒、事件、轉換和封送處理 \(Marshaling\) 等方面。  
  
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)  
 討論可用來將 COM 型別程式庫中找到的型別定義轉換為 Common Language Runtime 組件中對等定義的工具。