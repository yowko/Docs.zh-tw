---
title: "/reference (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/reference"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/r compiler option [C#]"
  - "reference compiler option [C#]"
  - "r compiler option [C#]"
  - "/reference compiler option [C#]"
  - "-r compiler option [C#]"
  - "metadata import [C#]"
  - "public type information [C#]"
  - "-reference compiler option [C#]"
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /reference (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/reference** 選項會讓編譯器將指定之檔案中的 [public](../../../csharp/language-reference/keywords/public.md) 型別資訊匯入目前的專案，使您得以從指定的組件檔案中參考中繼資料 \(Metadata\)。  
  
## 語法  
  
```  
/reference:[alias=]filename  
/reference:filename  
```  
  
## 引數  
 `filename`  
 含有組件資訊清單 \(Assembly Manifest\) 的檔案名稱。  若要匯入一個以上的檔案，請分別在每個檔案中加入 **\/reference** 選項。  
  
 `alias`  
 有效的 C\# 識別項代表根命名空間，其中會包含組件中的所有命名空間。  
  
## 備註  
 若要從一個以上的檔案匯入，請在每個檔案都加入 **\/reference** 選項。  
  
 匯入的檔案必須包含資訊清單，輸出檔案必須使用 [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 以外的其中一個 [\/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) 選項編譯。  
  
 **\/r** 是 **\/reference** 的簡短形式。  
  
 使用 [\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) 從不包含組件資訊清單的輸出檔中匯入中繼資料 \(Metadata\)。  
  
 如果您參考的組件 \(A 組件\) 本身也要參考其他組件 \(B 組件\) 的話，在下列情況下您必須參考 B 組件：  
  
-   您從 A 組件使用的型別繼承自某個型別，或是從 B 組件實作介面  
  
-   您從 B 組件叫用具有傳回型別 \(Return Type\) 或參數型別的欄位、屬性 \(Property\)、事件或方法  
  
 請使用 [\/lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) 指定一或多個組件參考所在的目錄。  **\/lib** 主題也提供了編譯器會在哪些目錄搜尋組件的相關討論。  
  
 如果要讓編譯器辨認組件 \(而非模組\) 中的某個型別，則必須強制它解析這個型別，您可以藉由定義該型別的執行個體來進行這種強制解析。  為編譯器解決組件中的型別名稱還有其他方法可行，例如，如果您是從組件中的型別繼承，編譯器隨後即可辨認型別名稱。  
  
 有時候，在單一組件內部參考同樣元件的兩種版本是必要的。  若要這麼做，請為每個檔案使用 **\/reference** 參數上的別名子選項，以分辨兩個檔案。  這個別名會用來當做元件名稱的限定詞，並會解析為其中一個檔案中的元件。  
  
 根據預設，會使用參考 .NET Framework 常用組件的 csc.rsp 回應檔 \(Response File\)。  如果您不要讓編譯器使用 csc.rsp，請使用 [\/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)。  
  
> [!NOTE]
>  在 Visual Studio 中，使用 \[**新增參照**\] 對話方塊。  如需詳細資訊，請參閱 [如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。  在 Visual Studio 2010 和更新版本中，為確保使用 `/reference` 新增參照 和使用 \[**新增參照**\] 對話方塊新增參照會有相同的行為，必須將您要新增的組件之 **Embed Interop Types** 屬性設為 **false**。  **True** 是該屬性的預設值。  
  
## 範例  
 這個範例示範如何使用[外部別名](../../../csharp/language-reference/keywords/extern-alias.md)功能。  
  
 您編譯原始程式檔，並從先前已編譯的 `grid.dll` 和 `grid20.dll` ``  匯入中繼資料。  兩個 DLL 包含相同元件的不同版本，而您使用兩個 **\/reference** 搭配別名選項，以編譯原始程式檔。  選項會如下所示：  
  
 \/reference:GridV1\=grid.dll and \/reference:GridV2\=grid20.dll  
  
 這會建立外部別名 "GridV1" 和 "GridV2"，而您可以在程式中以 extern 陳述式使用它們：  
  
```  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 完成後，您可以在控制名稱加上 GridV1 字首，並參考 grid.dll 中的方格控制項，方法如下：  
  
```  
GridV1::Grid  
```  
  
 此外，您可以在控制名稱加上 GridV2 字首，並參考 Grid20.dll 中的方格控制項，方法如下：  
  
```  
GridV2::Grid   
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)