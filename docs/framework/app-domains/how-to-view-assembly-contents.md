---
title: "如何：檢視組件內容"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9c12c4811e8b23e86fca3960acdb4da06e38fbe
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-view-assembly-contents"></a>如何：檢視組件內容
您可以使用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢視檔案中的 Microsoft 中繼語言 (MSIL) 資訊。 如果所檢查的檔案是組件，這項資訊可以包括組件的屬性，以及其他模組和組件的參考。 這項資訊可能有助於判斷檔案是組件還是組件的一部分，以及檔案是否有其他模組或組件的參考。  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a>使用 Ildasm.exe 顯示組件的內容  
  
1.  在命令提示字元鍵入 **ildasm** \<組件名稱>。 例如，下列命令會反組譯 `Hello.exe` 組件。  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a>檢視組件資訊清單資訊  
  
1.  按兩下 [MSIL 反組譯工具] 視窗中的資訊清單圖示。  
  
## <a name="example"></a>範例  
 下列範例會啟動基本 "Hello, World" 程式。 編譯程式之後，請使用 Ildasm.exe 來反組譯 Hello.exe 組件，以及檢視組件資訊清單。  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 在 Hello.exe 組件上執行命令 ildasm.exe，並按兩下 IL DASM 視窗中的資訊清單圖示，以產生下列輸出：  
  
```  
// Metadata version: v4.0.30319  
.assembly extern mscorlib  
{  
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..  
  .ver 4:0:0:0  
}  
.assembly Hello  
{  
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )   
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx  
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.  
  .hash algorithm 0x00008004  
  .ver 0:0:0:0  
}  
.module Hello.exe  
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}  
.imagebase 0x00400000  
.file alignment 0x00000200  
.stackreserve 0x00100000  
.subsystem 0x0003       // WINDOWS_CUI  
.corflags 0x00000001    //  ILONLY  
// Image base: 0x00600000  
```  
  
 下表描述範例中所用 Hello.exe 組件之組件資訊清單中的每個指示詞。  
  
|指示詞|描述|  
|---------------|-----------------|  
|**.assembly extern \<**組件名稱**>**|指定另一個組件，其中包含目前模組所參考的項目 (在此範例中為 `mscorlib`)。|  
|**.publickeytoken \<**權杖**>**|指定所參考組件之實際金鑰的權杖。|  
|**.ver \<**版本號碼**>**|指定所參考組件的版本號碼。|  
|**.assembly \<**組件名稱**>**|指定組件名稱。|  
|**.hash algorithm \<**int32 值**>**|指定使用的雜湊演算法。|  
|**.ver \<**版本號碼**>**|指定組件的版本號碼。|  
|**.module \<**檔案名稱**>**|指定構成組件之模組的名稱。 在此範例中，組件只包含一個檔案。|  
|**.subsystem \<**值**>**|指定程式所需的應用程式環境。 在此範例中，值 3 指出從主控台執行這個可執行檔。|  
|**.corflags**|中繼資料中目前保留的欄位。|  
  
 根據組件的內容，組件資訊清單可以包含許多不同的指示詞。 如需組件資訊清單中的指示詞延伸清單，請參閱 ECMA 文件，特別是 "Partition II: Metadata Definition and Semantics" (分割 II：中繼資料定義和語意) 和 "Partition III: CIL Instruction Set" (分割 III：CIL 指令集)。 您可以線上取得這份文件；請參閱 MSDN 上的 [ECMA C# 和通用語言基礎結構標準](http://go.microsoft.com/fwlink/?LinkID=99212)，以及 Ecma International 網站上的[標準 ECMA-335 - 通用語言基礎結構 (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552)。  
  
## <a name="see-also"></a>請參閱  
 [應用程式定義域和組件](http://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)  
 [應用程式定義域和組件操作說明主題](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
