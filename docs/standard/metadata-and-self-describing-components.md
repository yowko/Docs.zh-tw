---
title: "中繼資料和自我描述元件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- runtime, metadata
- languages, interoperability
- portable executable files, metadata
- self-describing files
- metadata, about metadata
- common language runtime, metadata
- PE files, metadata
- components [.NET Framework], metadata
ms.assetid: 3dd13c5d-a508-455b-8dce-0a852882a5a7
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ac08dcf305e8cc0c1a3be3b8300ed9981e7d84d4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="metadata-and-self-describing-components"></a>中繼資料和自我描述元件
在過去，以一種語言撰寫的軟體元件 (.exe 或 .dll) 不容易使用以另一種語言所撰寫的軟體元件。 COM 對這個問題提供了進一步的解決方式。 .NET Framework 允許編譯器 (Compiler) 發出額外的宣告資訊至所有模組和組件中，使元件的互通性更為容易。 這個資訊，稱為中繼資料 (Metadata)，能幫助元件順暢地互動。  
  
 中繼資料為二進位資訊，描述儲存在 Common Language Runtime 可移植執行檔 (PE) 或記憶體中的程式。 當您編譯程式碼為 PE 檔時，中繼資料被插入至檔案的一個部分，而您的程式碼則轉換至 Microsoft Intermediate Language (MSIL) 並插入至檔案的另一部分。 模組或組件中所定義和參考的一切型別和成員都描述於中繼資料內。 當執行程式碼時，Runtime 載入中繼資料至記憶體中，並參考它以探索您程式碼的類別、成員、繼承 (Inheritance) 等等的資訊。  
  
 中繼資料會描述您程式碼中以語言中性方式定義的每一個型別和成員。 中繼資料儲存下列資訊：  
  
-   組件的說明  
  
    -   識別 (名稱、版本、文化特性、公開金鑰)  
  
    -   匯出的型別  
  
    -   這個組件所依存的其他組件  
  
    -   執行所需要的安全性權限  
  
-   型別的說明  
  
    -   名稱、可視性、基底類別和實作的介面  
  
    -   成員 (方法、欄位、屬性、事件、巢狀型別)  
  
-   屬性  
  
    -   修改型別和成員的額外描述項目  
  
## <a name="benefits-of-metadata"></a>中繼資料的優點  
 中繼資料是較簡單的程式撰寫模型 (Programming Model) 的關鍵，排除對介面定義語言 (IDL) 檔案、標頭檔 (Header File) 或元件參考的任何外部方法的需要。 中繼資料可以讓 .NET Framework 語言自動以語言中性方式描述它們自己，而不讓開發人員及使用者看見。 此外，中繼資料透過屬性的使用會成為可擴充的。 中繼資料提供下列主要好處：  
  
-   自我描述檔案  
  
     Common Language Runtime 模組和組件為自我描述的。 模組的中繼資料包含與另一個模組互動的一切所需。 中繼資料自動提供 COM 中的 IDL 的功能，允許您將一個檔案當做定義及實作使用。 Runtime 模組和組件甚至不需要向作業系統註冊。 結果，Runtime 使用的描述永遠反應您編譯檔案中的實際程式碼，這樣即增加了應用程式的可靠性。  
  
-   語言互通性 (Interoperability) 和較容易的元件架構設計  
  
     中繼資料提供已編譯程式碼所需的全部資訊，讓您從不同語言撰寫的 PE 檔繼承類別。 您可以為任何 Managed 語言 (任何以 Common Language Runtime 為目標的語言) 所撰寫的任何類別建立執行個體，而不需擔心自訂互通性程式碼的明確封送處理 (Marshaling) 或使用。  
  
-   屬性  
  
     .NET Framework 允許您在已編譯的檔案中宣告稱為屬性的特定種類中繼資料。 屬性普遍存在於 .NET Framework，並且被用來更仔細控制您程式在 Run Time 的行為。 此外，您可以透過使用者定義的自訂屬性，發出您自己的自訂中繼資料至 .NET Framework 檔案中。 如需詳細資訊，請參閱[屬性](../../docs/standard/attributes/index.md)。  
  
## <a name="metadata-and-the-pe-file-structure"></a>中繼資料和 PE 檔結構  
 中繼資料是儲存在 .NET Framework 可移植執行檔 (PE) 的一個區段中，而 Microsoft Intermediate Language (MSIL) 則是儲存在 PE 檔的另一個區段。 檔案的中繼資料部分包含一系列表格和堆積 (Heap) 資料結構。 MSIL 部分包含參考 PE 檔中繼資料部分的 MSIL 和中繼資料語彙基元 (Token)。 當您使用 [MSIL 反組譯工具 (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) 等工具來檢視程式碼的 MSIL 時，可能遇到中繼資料語彙基元。  
  
### <a name="metadata-tables-and-heaps"></a>中繼資料表和堆積  
 各個中繼資料表都儲存您程式項目的資訊。 例如，某個中繼資料表描述您程式碼的類別，而另一個表格則描述欄位等等。 如果您的程式碼中有十個類別，類別表格將會有十列，一列對應一個類別。 中繼資料表會參考其他表格和堆積。 例如，類別的中繼資料表會參考方法的表格。  
  
 中繼資料也將資訊儲存在四種堆積結構中：字串、BLOB (二進位大型物件)、使用者字串和 GUID。 所有用於命名型別和成員的字串都儲存在字串堆積中。 例如，方法表格不直接儲存特定方法的名稱，但指向儲存在字串堆積中的方法名稱。  
  
### <a name="metadata-tokens"></a>中繼資料語彙基元  
 各個中繼資料表的每一列在 PE 檔的 MSIL 部分由中繼資料語彙基元來唯一辨識。 中繼資料語彙基元在概念上類似指標，它保存 (Persist) 在 MSIL 中，並參考特定中繼資料表。  
  
 中繼資料語彙基元為四位元組數字。 第一個位元組代表特定語彙基元所參考的中繼資料表 (方法、型別等等)。 剩餘三個位元組指定中繼資料表中的列，對應正在描述的程式設計項目。 如果您以 C# 定義方法，並編譯它為 PE 檔，下列中繼資料語彙基元可能存在於 PE 檔的 MSIL 部分：  
  
```  
0x06000004  
```  
  
 第一個位元組 (`0x06`) 表示這是 **MethodDef** 語彙基元。 下面的三個位元組 (`000004`) 會告知 Common Language Runtime 到 **MethodDef** 表格的第四列來尋找說明這個方法定義的資訊。  
  
### <a name="metadata-within-a-pe-file"></a>PE 檔內的中繼資料  
 當編譯 Common Language Runtime 的程式時，它被轉換至由三部分組成的 PE 檔。 下表說明各部分的內容。  
  
|PE 區段|PE 區段的內容|  
|----------------|----------------------------|  
|PE 標頭|PE 檔主要區段的索引和進入點 (Entry Point) 的位址。<br /><br /> 執行階段會使用這個資訊辨識檔案為 PE 檔，並決定當載入程式至記憶體時，於何處開始執行。|  
|MSIL 指令|構成您程式碼的 Microsoft Intermediate Language 指令 (MSIL)。 許多 MSIL 指令都有中繼資料語彙基元伴隨。|  
|中繼資料|中繼資料表和堆積。 執行階段會使用這個區段來記錄您程式碼中一切型別和成員的資訊。 這個區段也包括自訂屬性和安全性資訊。|  
  
## <a name="run-time-use-of-metadata"></a>中繼資料的執行階段使用  
 若要更了解中繼資料和它在 Common Language Runtime 中的角色，建構簡單程式並說明中繼資料如何影響它的執行階段存留期，可能很有幫助。 下列程式碼範例展示稱為 `MyApp` 的類別內的兩個方法。 `Main` 方法為程式進入點，而 `Add` 方法只是傳回兩個整數引數的總和。  
  
```vb  
Public Class MyApp  
   Public Shared Sub Main()  
      Dim ValueOne As Integer = 10  
      Dim ValueTwo As Integer = 20  
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo))  
   End Sub  
  
   Public Shared Function Add(One As Integer, Two As Integer) As Integer  
      Return (One + Two)  
   End Function  
End Class  
```  
  
```csharp  
using System;    
public class MyApp  
{  
   public static int Main()  
   {  
      int ValueOne = 10;  
      int ValueTwo = 20;           
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo));  
      return 0;  
   }  
   public static int Add(int One, int Two)  
   {  
      return (One + Two);  
   }  
}  
```  
  
 當執行程式碼時，Runtime 將模組載入記憶體，並查閱中繼資料以取得這個類別。 一旦載入後，Runtime 會對該方法的 Microsoft Intermediate Language (MSIL) 資料流做一個廣泛的分析，以將它轉換為快速的原生機器指令。 Runtime 使用 Just-in-Time (JIT) 編譯器，按所需一次一個的方法轉換 MSIL 指令至原生機器碼 (Machine Code)。  
  
 下列範例展示從前面程式碼的 `Main` 函式產生的部分 MSIL。 您可以使用 [MSIL 反組譯工具 (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢視任何 .NET Framework 應用程式中的 MSIL 和中繼資料。  
  
```  
.entrypoint  
.maxstack  3  
.locals ([0] int32 ValueOne,  
         [1] int32 ValueTwo,  
         [2] int32 V_2,  
         [3] int32 V_3)  
IL_0000:  ldc.i4.s   10  
IL_0002:  stloc.0  
IL_0003:  ldc.i4.s   20  
IL_0005:  stloc.1  
IL_0006:  ldstr      "The Value is: {0}"  
IL_000b:  ldloc.0  
IL_000c:  ldloc.1  
IL_000d:  call int32 ConsoleApplication.MyApp::Add(int32,int32) /* 06000003 */  
```  
  
 JIT 編譯器會讀取整個方法的 MSIL、全面分析它，並產生那個方法的有效率的原生指令。 在 `IL_000d` 上會遇到 `Add` 方法的中繼資料語彙基元 (`/*` `06000003 */`)，而執行階段即利用語彙基元查閱 **MethodDef** 表格的第三列。  
  
 下表顯示 **MethodDef** 表格中，由描述 `Add` 方法的中繼資料語彙基元所參考的部分。 雖然尚有其他中繼資料表存在於這個組件中並擁有其唯一值，但只有這個表格在討論之列。  
  
|表格列|相關的虛擬位址 (RVA)|ImplFlags|旗標|名稱<br /><br /> (指向字串堆積)|簽章 (指向 BLOB 堆積)|  
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|  
|1|0x00002050|IL<br /><br /> Managed|Public<br /><br /> ReuseSlot<br /><br /> SpecialName<br /><br /> RTSpecialName<br /><br /> .ctor|.ctor (建構函式)||  
|2|0x00002058|IL<br /><br /> Managed|Public<br /><br /> Static<br /><br /> ReuseSlot|主要|String|  
|3|0x0000208c|IL<br /><br /> Managed|Public<br /><br /> Static<br /><br /> ReuseSlot|新增|int, int, int|  
  
 表格的每一欄包含您程式碼的重要資訊。 **RVA** 欄允許執行階段計算定義這個方法之 MSIL 的起始記憶體位址。 **ImplFlags** 和 **Flags** 欄包含描述方法的位元遮罩 (例如，方法為 Public 或 Private)。 **Name** 欄對字串堆積中的方法名稱進行索引。 **Signature** 欄對 Blob 堆積中方法簽章的定義進行索引。  
  
 執行階段計算第三列中 **RVA** 欄的所需位移位址，並傳回這個位址到 JIT 編譯器，並接著進入新位址。 JIT 編譯器在新位址繼續處理 MSIL 直到遭遇另一個中繼資料語彙基元，並重複這過程。  
  
 藉著使用中繼資料，Runtime 擁有對載入您程式碼所需全部資訊的存取權，並處理它成為原生機器指令。 以這個方式，中繼資料允許自我描述檔案和連同一般型別系統的跨語言繼承。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[屬性](../../docs/standard/attributes/index.md)|描述如何套用屬性、撰寫自訂屬性和擷取儲存於屬性的資訊。|
