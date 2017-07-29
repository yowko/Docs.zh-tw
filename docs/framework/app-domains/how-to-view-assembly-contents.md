---
title: "如何：檢視組件內容 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "組件資訊清單，檢視資訊"
  - "Ildasm.exe"
  - "MSIL 反組譯工具"
  - "組件 [.NET Framework]，檢視內容"
  - "檢視組件資訊"
  - "MSIL"
  - "檢視 MSIL 資訊"
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：檢視組件內容
您可以使用 [Ildasm.exe \(IL Disassembler\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢視檔案中的 Microsoft Intermediate Language \(MSIL\) 資訊。  如果您所檢查的檔案是組件，該資訊將包括組件的屬性，以及對其他模組和組件的參考。  該資訊有助於判斷檔案是否為組件或為組件的一部分，以及檔案是否參考其他模組或組件。  
  
### 若要使用 Ildasm.exe 顯示組件內容  
  
1.  在命令提示字元中輸入 **ildasm** \<*assembly name*\>。  例如，下列命令可以反組譯 `Hello.exe` 組件：  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### 若要檢視組件資訊清單資訊  
  
1.  按兩下 \[MSIL 反組譯工具\] 視窗中的 MANIFEST 圖示。  
  
## 範例  
 下列範例從基本的 "Hello, World" 程式開始。  編譯程式之後，請使用 Ildasm.exe 來反組譯 Hello.exe 組件並檢視組件資訊清單。  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 對 Hello.exe 組件執行 ildasm.exe 命令，並在 \[IL DASM\] 視窗中按兩下 MANIFEST 圖示，以產生下列輸出：  
  
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
  
 下表說明範例所使用的 Hello.exe 組件資訊清單中的所有指示詞。  
  
|指示詞|說明|  
|---------|--------|  
|**.assembly extern \<** *assembly name* **\>**|指定其他組件，該組件含有目前模組所參考的項目 \(在這個範例中為 `mscorlib`\)|  
|**.publickeytoken \<** *token* **\>**|指定參考組件的實際金鑰語彙基元|  
|**.ver \<** *version number* **\>**|指定參考組件的版本編號|  
|**.assembly \<** *assembly name* **\>**|指定組件名稱|  
|**.hash algorithm \<** *int32 value* **\>**|指定使用的雜湊演算法|  
|**.ver \<** *version number* **\>**|指定組件的版本號碼|  
|**.module \<** *file name* **\>**|指定構成組件的模組名稱。  在這個範例中，組件只由一個檔案組成|  
|**.subsystem \<** *value* **\>**|指定程式所需的應用程式環境。  在這個範例中，3 表示該可執行檔是從主控台執行|  
|**.corflags**|中繼資料中目前保留的欄位|  
  
 組件資訊清單可包含許多不同的指示詞，視組件的內容而定。  如需組件資訊清單中指示詞的詳細清單，請參閱 ECMA 文件，特別是＜Partition II: Metadata Definition and Semantics＞和＜Partition III: CIL Instruction Set＞這兩部分。  您可以線上取得這份文件；請於MSDN參閱 [ECMA C\# 和通用語言基礎結構標準](http://go.microsoft.com/fwlink/?LinkID=99212) 以及在ECMA國際化網站上的  [標準 ECMA\-335 \- Common Language Infrastructure \(CLI\)](http://go.microsoft.com/fwlink/?LinkID=65552) 。  
  
## 請參閱  
 [Application Domains and Assemblies](http://msdn.microsoft.com/zh-tw/433b04ae-4ba8-4849-9dbd-79194f240346)   
 [應用程式定義域和組件 HOW TO 主題](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)   
 [Ildasm.exe \(IL Disassembler\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)