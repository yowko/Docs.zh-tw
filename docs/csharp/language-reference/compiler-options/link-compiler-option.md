---
title: "/link (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/l compiler option [C#]"
  - "/link compiler option [C#]"
  - "-l compiler option [C#]"
  - "EmbedInteropTypes"
  - "l compiler option [C#]"
  - "embed interop types [COM Interop]"
  - "-link compiler option [C#]"
  - "link compiler option [C#]"
ms.assetid: 00da70c6-9ea1-43c2-86f2-aa7f26c03475
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# /link (C# Compiler Options)
讓編譯器允許您目前正在編譯的專案使用指定組件中的 COM 型別資訊。  
  
## 語法  
  
```  
/link:fileList  
// -or-  
/l:fileList  
```  
  
## 引數  
 `fileList`  
 必要項。  逗號分隔的組件檔名清單。  如果檔案名稱包含空格，請將名稱加上雙引號 \(" "\)。  
  
## 備註  
 `/link` 可讓您部署具有內嵌型別資訊的應用程式。  應用程式因此可以使用實作內嵌型別資訊之執行階段組件中的型別，而不需要參考執行階段組件。  如果執行階段組件有許多發行版本，包含內嵌型別資訊的應用程式就可以在沒有重新編譯的情況下，使用各種版本的組件。  如需範例，請參閱 [逐步解說：從 Managed 組件內嵌類型](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 當您在使用 COM Interop 時，使用 `/link` 選項會特別有用。  您可以內嵌 COM 型別，這樣目標電腦便不再需要主要 Interop 組件 \(PIA\)，同時也能執行應用程式。  `/link` 選項會指示編譯器將所參考 Interop 組件的 COM 型別資訊內嵌至編譯產生的程式碼中。  COM 型別是由 CLSID \(GUID\) 值來識別。  因此，應用程式可以在已安裝含相同 CLSID 值之相同 COM 型別的目標電腦上執行。  自動化 Microsoft Office 的應用程式是很好的範例。  像 Office 這樣的應用程式通常會在不同版本間保持相同的 CLSID 值，因此只要目標電腦上有安裝 .NET Framework 4 \(含\) 以後版本，且應用程式使用包含在所參考 COM 型別中的方法、屬性或事件，應用程式就可以使用這些參考的 COM 型別。  
  
 `/link` 選項只能內嵌介面、結構和委派，  不支援內嵌 COM 類別。  
  
> [!NOTE]
>  當您在程式碼中建立內嵌 COM 型別的執行個體時，必須使用適當的介面來建立執行個體。  嘗試使用 CoClass 建立內嵌 COM 型別的執行個體將會導致錯誤。  
  
 若要設定 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 中的 `/link` 選項，請加入組件參考，並將 `Embed Interop Types` 屬性設定為 **true**。  `Embed Interop Types` 屬性的預設值為 **false**。  
  
 當連結至本身參考其他 COM 組件 \(B 組件\) 的 COM 組件 \(A 組件\) 時，如果符合下列任一情況，您也必須連結至 B 組件：  
  
-   來自 A 組件的型別繼承自某個型別，或是從 B 組件實作介面。  
  
-   從 B 組件叫用 \(Invoke\) 具有傳回型別或參數型別的欄位、屬性 \(Property\)、事件或方法。  
  
 如同 [\/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) 編譯器選項，`/link` 編譯器選項也會使用參考常用 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 組件的 Csc.rsp 回應檔。  如果您不要讓編譯器使用 Csc.rsp 檔，請使用 [\/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) 編譯器選項。  
  
 `/link` 的簡短形式為 `/l`。  
  
## 泛型和內嵌型別  
 下列章節將說明在內嵌 Interop 型別的應用程式中使用泛型型別時的限制。  
  
### 泛型介面  
 無法使用從 Interop 組件內嵌的泛型介面。  這在下列範例中顯示。  
  
 [!code-cs[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/csharp/vblinkcompilercs/program.cs#1)]  
  
### 具有泛型參數的型別  
 如果具有泛型參數的型別來自外部組件，且其參數的型別是從 Interop 組件內嵌的，則無法使用該型別。  這項限制不適用於介面。  例如，試想在 <xref:Microsoft.Office.Interop.Excel> 組件中定義的 <xref:Microsoft.Office.Interop.Excel.Range> 介面。  如果程式庫內嵌來自 <xref:Microsoft.Office.Interop.Excel> 組件的 Interop 型別，並公開傳回泛型型別的方法，但是此泛型型別具有型別為 <xref:Microsoft.Office.Interop.Excel.Range> 介面的參數，那麼這個方法就必須傳回泛型介面，如下列程式碼範例所示。  
  
 [!code-cs[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/csharp/vblinkcompilercs/utility.cs#2)]  
[!code-cs[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/csharp/vblinkcompilercs/utility.cs#3)]  
[!code-cs[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/csharp/vblinkcompilercs/utility.cs#4)]  
  
 在下列範例中，用戶端程式碼可以呼叫傳回 <xref:System.Collections.IList> 泛型介面的方法，且不會發生錯誤。  
  
 [!code-cs[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/csharp/vblinkcompilercs/program.cs#5)]  
  
## 範例  
 下列程式碼會編譯原始程式檔 `OfficeApp.cs`，並參考 `COMData1.dll` 和 `COMData2.dll` 中的組件來產生 `OfficeApp.exe`。  
  
```c#  
csc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.cs  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [逐步解說：從 Managed 組件內嵌類型](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [\/reference \(Import Metadata\)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)   
 [\/noconfig \(Ignore csc.rsp\)](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)   
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [互通性概觀](../../../csharp/programming-guide/interop/interoperability-overview.md)