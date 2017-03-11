---
title: "/warnaserror (Visual Basic) | Microsoft Docs"
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
  - "warnaserror compiler option [Visual Basic]"
  - "/warnaserror compiler option [Visual Basic]"
  - "-warnaserror compiler option [Visual Basic]"
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# /warnaserror (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

會使編譯器將第一個出現的警告當做錯誤。  
  
## 語法  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|\+ &#124; \-|選擇項。  `/warnaserror-` 預設會生效，警告並不會阻止編譯器產生輸出檔。  `/warnaserror`  選項和 `/warnaserror+` 一樣，都會使警告被視為錯誤。|  
|`numberList`|選擇項。  `/warnaserror` 選項所適用之逗號分隔的警告 ID 號碼清單。  如果未指定警告 ID，則 `/warnaserror` 選項適用於所有警告。|  
  
## 備註  
 `/warnaserror` 選項會將所有警告視為錯誤。  任何正常情況下會被報告為警告的訊息都會被報告為錯誤。  編譯器會將後續發生的相同警告報告為警告。  
  
 `/warnaserror-` 預設會生效，而這讓警告變成僅供參考。  `/warnaserror`  選項和 `/warnaserror+` 一樣，都會使警告被視為錯誤。  
  
 如果您只要將少數的特定警告視為錯誤，可以指定以逗號分隔的清單，列出要視為錯誤的警告編號。  
  
> [!NOTE]
>  `/warnaserror` 選項不會控制警告的顯示方式。  使用 [\/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) 選項停用警告。  
  
||  
|-|  
|若要設定 \/warnaserror 將所有警告視為 Visual Studio IDE 中的錯誤|  
|1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.  按一下 \[**編譯**\] 索引標籤。<br />3.  確定未核取 \[**停用所有警告**\] 核取方塊。<br />4.  核取 \[**將所有警告視為錯誤**\] 核取方塊。|  
  
||  
|-|  
|若要設定 \/warnaserror 將特定警告視為 Visual Studio IDE 中的錯誤|  
|1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。<br />2.  按一下 \[**編譯**\] 索引標籤。<br />3.  確定未核取 \[**停用所有警告**\] 核取方塊。<br />4.  確定未核取 \[**將所有警告視為錯誤**\] 核取方塊。<br />5.  從與應視為錯誤之警告相鄰的 \[**告知**\] 資料行中選取 \[**錯誤**\]。|  
  
## 範例  
 下列程式碼會編譯 `In.vb`，並指示編譯器將它所找到的每一個第一次出現的警告顯示為錯誤。  
  
```  
vbc /warnaserror in.vb  
```  
  
## 範例  
 下列程式碼會編譯 `T2.vb` 並只將未使用區域變數的警告 \(42024\) 視為錯誤。  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)