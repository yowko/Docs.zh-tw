---
title: "Access Levels in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "members, accessing in Visual Basic"
  - "Friend access modifier"
  - "access levels, declared elements"
  - "access levels"
  - "access modifiers"
  - "Public access modifier"
  - "Protected access modifier"
  - "Protected Friend access modifier"
  - "Private access modifier"
  - "declared elements, access level"
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Access Levels in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

宣告項目的「*存取層級*」\(Access Level\) 表示對項目進行存取的能力範圍，也就代表哪些程式碼對項目具有讀寫權限。  這不只是取決於您宣告項目本身的方式，也需視項目容器 \(Container\) 的存取層級而定。  不能存取包含項目的程式碼，也就無法存取其所包含的任何項目，即使所包含的項目是宣告為 `Public`。  例如，在 `Private` 結構中的 `Public` 變數可從包含該結構的類別內存取，但無法從該類別外存取。  
  
## Public  
 宣告陳述式中的 [Public](../../../../visual-basic/language-reference/modifiers/public.md) 關鍵字會指定該項目可從相同專案、從參考該專案的其他專案和從該專案所建置的組件內的任何地方存取。  下列程式碼說明 `Public` 宣告的範例。  
  
```  
Public Class classForEverybody  
```  
  
 您只能在模組、介面或命名空間層級使用 `Public`。  這表示您可以在原始程式檔或命名空間層級，或者是介面、模組、類別或結構內宣告 public 項目，但不可以在程序內宣告該項目。  
  
## Protected  
 宣告陳述式中的 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) 關鍵字會指定該項目只能從相同類別或從該類別的衍生類別中存取。  下列程式碼說明 `Protected` 宣告的範例。  
  
```  
Protected Class classForMyHeirs  
```  
  
 您只能在類別層級使用 `Protected`，而且只能在宣告類別的成員時使用。  這表示您可以在類別中宣告 protected 項目，但不可以在原始程式檔或命名空間層級，或者是介面、模組、結構或程序內宣告該項目。  
  
## Friend  
 宣告陳述式中的 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) 關鍵字會指定該項目可從相同組件內存取，但不可以從組件以外存取。  下列程式碼說明 `Friend` 宣告的範例。  
  
```  
Friend stringForThisProject As String  
```  
  
 您只能在模組、介面或命名空間層級使用 `Friend`。  這表示您可以在原始程式檔或命名空間層級，或者是介面、模組、類別或結構內宣告 friend 項目，但不可以在程序內宣告該項目。  
  
## Protected Friend  
 宣告陳述式中同時出現 `Protected` 和 `Friend` 關鍵字，會指定該項目可從衍生類別、相同組件或兩者內存取。  下列程式碼說明 `Protected` `Friend` 宣告的範例。  
  
```  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 您只能在類別層級使用 `Protected` `Friend`，而且只能在宣告類別的成員時使用。  這表示您可以在類別中宣告 protected friend 項目，但不可以在原始程式檔或命名空間層級，或者是介面、模組、結構或程序內宣告該項目。  
  
## Private  
 宣告陳述式中的 [Private](../../../../visual-basic/language-reference/modifiers/private.md) 關鍵字會指定該項目只能從相同模組、類別或結構內存取。  下列程式碼說明 `Private` 宣告的範例。  
  
```  
Private numberForMeOnly As Integer  
```  
  
 只能在模組層級使用 `Private`。  這表示您可以在模組、類別或結構中宣告 private 項目，但不可以在原始程式檔或命名空間層級，或者是介面或程序內宣告該項目。  
  
 在模組層級中，沒有任何存取層級關鍵字的 `Dim` 陳述式跟 `Private` 宣告是一樣的。  但是，您可能會想要用 `Private` 關鍵字使您的程式碼更容易讀取與解譯。  
  
## 存取修飾詞  
 表示存取層級的關鍵字稱為「*存取修飾詞*」\(Access Modifier\)。  下表對存取修飾詞進行比較。  
  
|存取修飾詞|授與的存取層級|可以使用此存取層級宣告的項目|可以使用此修飾詞的宣告內容|  
|-----------|-------------|--------------------|-------------------|  
|`Public`|不受限：<br /><br /> 任何程式碼只要可以看到 public 項目，都可以存取該項目|介面<br /><br /> 模組<br /><br /> 類別<br /><br /> 結構<br /><br /> 結構成員<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|原始程式檔<br /><br /> 命名空間<br /><br /> 介面<br /><br /> 模組<br /><br /> 類別<br /><br /> 結構|  
|`Protected`|衍生的：<br /><br /> 宣告 protected 項目的類別或其衍生類別內的程式碼，即可以存取該項目|介面<br /><br /> 類別<br /><br /> 結構<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|類別|  
|`Friend`|組件：<br /><br /> 宣告 friend 項目組件內的程式碼，即可以存取該項目|介面<br /><br /> 模組<br /><br /> 類別<br /><br /> 結構<br /><br /> 結構成員<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|原始程式檔<br /><br /> 命名空間<br /><br /> 介面<br /><br /> 模組<br /><br /> 類別<br /><br /> 結構|  
|`Protected` `Friend`|`Protected` 和 `Friend` 的結合：<br /><br /> 與 protected friend 項目位於相同類別或相同組件內，或者是該項目類別的任何衍生類別內的程式碼，即可以存取該項目|介面<br /><br /> 類別<br /><br /> 結構<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|類別|  
|`Private`|宣告內容：<br /><br /> 宣告 private 項目的型別內的程式碼，包括所包含型別內的程式碼，即可以存取該項目|介面<br /><br /> 類別<br /><br /> 結構<br /><br /> 結構成員<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|模組<br /><br /> 類別<br /><br /> 結構|  
  
## 請參閱  
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [How to: Control the Availability of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)   
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)