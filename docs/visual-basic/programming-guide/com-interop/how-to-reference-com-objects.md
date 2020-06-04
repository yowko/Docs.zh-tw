---
title: 如何：參考 Visual Basic 的 COM 物件
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 2e2cbac6fad5e1686b7383c44619b8c6f5326483
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396800"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>如何：參考 Visual Basic 的 COM 物件
在 Visual Basic 中，加入具有類型程式庫之 COM 物件的參考時，需要建立 COM 程式庫的 interop 元件。 COM 物件成員的參考會路由傳送至 interop 元件，然後轉送至實際的 COM 物件。 COM 物件的回應會路由傳送至 interop 元件，並轉送至您的 .NET Framework 應用程式。  
  
 您可以在 .NET 元件中內嵌 COM 物件的類型資訊，而不使用 interop 元件來參考 COM 物件。 若要內嵌類型資訊，請 `Embed Interop Types` `True` 針對 COM 物件的參考，將屬性設定為。 如果您要使用命令列編譯器進行編譯，請使用 `/link` 選項來參考 COM 程式庫。 如需詳細資訊，請參閱[-link （Visual Basic）](../../reference/command-line-compiler/link.md)。  
  
 當您從整合式開發環境（IDE）加入類型程式庫的參考時，Visual Basic 會自動建立 interop 元件。 從命令列工作時，您可以使用 Tlbimp.exe 公用程式來手動建立 interop 元件。  
  
### <a name="to-add-references-to-com-objects"></a>加入 COM 物件的參考  
  
1. 在 [**專案**] 功能表上，選擇 [**加入參考**]，然後按一下對話方塊中的 [ **COM** ] 索引標籤。  
  
2. 從 COM 物件清單中選取您想要使用的元件。  
  
3. 若要簡化 interop 元件的存取，請 `Imports` 在您將使用 COM 物件的類別或模組頂端新增語句。 例如，下列程式碼範例會匯入連結 `INKEDLib` 庫中所參考之物件的命名空間 `Microsoft InkEdit Control 1.0` 。  
  
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

- [COM Interop](index.md)
- [Tlbimp.exe （類型程式庫匯入工具）](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe （類型程式庫匯出工具）](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [逐步解說：實作 COM 物件的繼承](walkthrough-implementing-inheritance-with-com-objects.md)
- [疑難排解互通性的問題](troubleshooting-interoperability.md)
- [Imports 陳述式 (.NET 命名空間和類型)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
