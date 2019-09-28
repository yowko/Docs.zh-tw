---
title: HOW TO：從 Visual Basic 參考 COM 物件
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 8e502dc9a279d9271a61fd2cf7a6afb564f09125
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351993"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>HOW TO：從 Visual Basic 參考 COM 物件
在 Visual Basic 中，加入具有類型程式庫之 COM 物件的參考時，需要建立 COM 程式庫的 interop 元件。 COM 物件成員的參考會路由傳送至 interop 元件，然後轉送至實際的 COM 物件。 COM 物件的回應會路由傳送至 interop 元件，並轉送至您的 .NET Framework 應用程式。  
  
 您可以在 .NET 元件中內嵌 COM 物件的類型資訊，而不使用 interop 元件來參考 COM 物件。 若要內嵌類型資訊，請將 `Embed Interop Types` 屬性設定為 `True`，以取得 COM 物件的參考。 如果您使用命令列編譯器進行編譯，請使用 `/link` 選項來參考 COM 程式庫。 如需詳細資訊，請參閱[/link （Visual Basic）](../../../visual-basic/reference/command-line-compiler/link.md)。  
  
 當您從整合式開發環境（IDE）加入類型程式庫的參考時，Visual Basic 會自動建立 interop 元件。 從命令列工作時，您可以使用 Tlbimp.exe 公用程式來手動建立 interop 元件。  
  
### <a name="to-add-references-to-com-objects"></a>加入 COM 物件的參考  
  
1. 在 [**專案**] 功能表上，選擇 [**加入參考**]，然後按一下對話方塊中的 [ **COM** ] 索引標籤。  
  
2. 從 COM 物件清單中選取您想要使用的元件。  
  
3. 若要簡化 interop 元件的存取，請在您將使用 COM 物件的類別或模組頂端新增 `Imports` 語句。 例如，下列程式碼範例會針對 `Microsoft InkEdit Control 1.0` 程式庫中所參考的物件，匯入 `INKEDLib` 的命名空間。  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>若要使用 Tlbimp 建立 interop 元件  
  
1. 將 Tlbimp 的位置新增至搜尋路徑（如果它還不是搜尋路徑的一部分，而且您目前不在其所在的目錄中）。  
  
2. 從命令提示字元呼叫 Tlbimp，並提供下列資訊：  
  
    - 包含類型程式庫的 DLL 名稱和位置  
  
    - 應放置資訊的命名空間名稱和位置  
  
    - 目標 interop 元件的名稱和位置  
  
     下列程式碼提供一個範例：  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     您可以使用 Tlbimp 來建立類型程式庫的 interop 元件，即使是未註冊的 COM 物件也是如此。 不過，interop 元件所參考的 COM 物件必須在要使用它們的電腦上正確註冊。 您可以使用 Windows 作業系統隨附的 Regsvr32 公用程式來註冊 COM 物件。  
  
## <a name="see-also"></a>另請參閱

- [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tlbimp.exe (類型程式庫匯入工具)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (類型程式庫匯出工具)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [逐步解說：實作 COM 物件的繼承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [互通性的疑難排解](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
