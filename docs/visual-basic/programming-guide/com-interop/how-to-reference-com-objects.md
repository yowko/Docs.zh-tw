---
title: "How to: Reference COM Objects from Visual Basic | Microsoft Docs"
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
  - "COM interop, referencing COM objects"
  - "referencing objects, COM objects from Visual Basic"
  - "objects [Visual Basic], referencing"
  - "COM objects, referencing"
  - "interop assemblies"
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Reference COM Objects from Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

在 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中加入具有型別程式庫的 COM 物件參考，需要先建立 COM 程式庫的 Interop 組件。  參考 COM 物件的成員會傳送到 Interop 組件，然後再傳至實質的 COM 物件。  COM 物件的回應會先傳送到 Interop 組件，然後再傳至您的 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 應用程式。  
  
 您可以將 COM 物件的型別資訊內嵌於 .NET 組件中，就能夠不使用 Interop 組件而參考 COM 物件。  若要內嵌型別資訊，請將 COM 物件參考的 `Embed Interop Types` 屬性設定為 `True`。  如果您是使用命令列編譯器進行編譯，請使用 `/link` 選項來參考 COM 程式庫。  如需詳細資訊，請參閱 [\/link](../../../visual-basic/reference/command-line-compiler/link.md)。  
  
 當您從整合式開發環境 \(IDE\) 加入型別程式庫的參考時，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會自動建立 Interop 組件。  當在命令列執行作業時，您可使用 Tlbimp 公用程式來手動建立 Interop 組件。  
  
### 若要將參考加入至 COM 物件  
  
1.  在 \[**專案**\] 功能表上選取 \[**加入參考**\]，然後按一下對話方塊中的 \[**COM**\] 索引標籤。  
  
2.  從 COM 物件的清單中選取要使用的元件。  
  
3.  為了簡化存取 Interop 組件，請將 `Imports` 陳述式加入至將使用 COM 物件的類別或模組的上方。  例如，下列程式碼範例會為 `Microsoft InkEdit Control 1.0` 程式庫中參考的物件匯入命名空間 `INKEDLib`。  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### 若要使用 Tlbimp 建立 Interop 組件  
  
1.  如果 Tlbimp 的位置還不是搜尋路徑的一部分，而且您目前不在其所在的目錄中，則請將它的位置加至搜尋路徑。  
  
2.  從命令提示字元呼叫 Tlbimp，提供下列資訊：  
  
    -   包含型別程式庫的 DLL 的名稱和位置  
  
    -   應放入資訊的命名空間 \(Namespace\) 的名稱和位置  
  
    -   目標 Interop 組件的名稱和位置  
  
     下列程式碼提供一個範例：  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     您可使用 Tlbimp 來建立型別程式庫的 Interop 組件，即使是針對未註冊的 COM 物件也行。  不過，Interop 組件參考的 COM 物件必須在使用它們的電腦上進行適當的註冊。  您可以使用 Windows 作業系統內含的 Regsvr32 公用程式來註冊 COM 物件。  
  
## 請參閱  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)   
 [Tlbexp.exe \(Type Library Exporter\)](../Topic/Tlbexp.exe%20\(Type%20Library%20Exporter\).md)   
 [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)