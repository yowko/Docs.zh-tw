---
title: "如何：參考 Visual Basic 的 COM 物件"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 694bd74e2b5ae374269accd845fe9178958bf56c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>如何：參考 Visual Basic 的 COM 物件
在[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]，將參考加入至具有型別程式庫的 COM 物件的 COM 程式庫需要建立 interop 組件。 COM 物件的成員的參考會路由傳送至的 interop 組件，接著再轉寄到實際的 COM 物件。 從 COM 物件的回應會路由傳送至的 interop 組件，並轉送至您[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]應用程式。  
  
 您可以參考 COM 物件，而不使用 interop 組件是.NET 組件中內嵌的 COM 物件的類型資訊。 若要將內嵌類型資訊，請設定`Embed Interop Types`屬性`True`的 COM 物件的參考。 如果您正在使用命令列編譯器來編譯，請使用`/link`參考的 COM 程式庫的選項。 如需詳細資訊，請參閱[/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)。  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]當您新增整合式的開發環境 (IDE) 中的類型程式庫的參考時，會自動建立 interop 組件。 從命令列時，您可以使用 Tlbimp 公用程式來手動建立 interop 組件。  
  
### <a name="to-add-references-to-com-objects"></a>將參考加入至 COM 物件  
  
1.  在**專案**功能表上，選擇**加入參考**，然後按一下  **COM**對話方塊索引標籤中的。  
  
2.  選取您想要從清單中的 COM 物件使用的元件。  
  
3.  若要簡化的存取權的 interop 組件，加入`Imports`頂端的類別或模組中，您會使用 COM 物件的陳述式。 例如，下列程式碼範例會匯入命名空間`INKEDLib`中參考的物件`Microsoft InkEdit Control 1.0`程式庫。  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>若要建立使用 Tlbimp interop 組件  
  
1.  如果還沒有的搜尋路徑的一部分，而且您目前不在其所在的目錄，加入搜尋路徑 Tlbimp 的位置。  
  
2.  呼叫 Tlbimp 從命令提示字元，提供下列資訊：  
  
    -   包含型別程式庫的 DLL 的名稱和位置  
  
    -   名稱和命名空間的位置資訊放置的位置  
  
    -   目標的 interop 組件的名稱和位置  
  
     下列程式碼提供一個範例：  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     您可以使用 Tlbimp 建立 interop 組件的類型程式庫，即使未註冊的 COM 物件。 不過，您必須正確他們要用來在電腦上註冊 interop 組件所參考的 COM 物件。 您可以使用 Regsvr32 公用程式隨附於 Windows 作業系統中註冊的 COM 物件。  
  
## <a name="see-also"></a>另請參閱  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (類型程式庫匯入工具)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 [Tlbexp.exe (類型程式庫匯出工具)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [逐步解說：實作 COM 物件的繼承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [互通性的疑難排解](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
