---
title: "/target:appcontainerexe (C# 編譯器選項) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# /target:appcontainerexe (C# 編譯器選項)
如果您使用 **\/target:appcontainerexe** 編譯器選項，編譯器會建立一個必須在應用程式容器中執行的 Windows 可執行檔 \(.exe\)。  這個選項相等於 [\/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)，但是專為 [!INCLUDE[win8_appname_long](../../../csharp/includes/win8-appname-long-md.md)]應用程式設計的。  
  
## 語法  
  
```  
/target:appcontainerexe  
```  
  
## 備註  
 這個選項會在[可攜式執行檔](http://go.microsoft.com/fwlink/p/?LinkId=236960) \(PE\) 檔案中設定一個位元，以要求應用程式在應用程式容器中執行。  當這個位元設定時，如果 CreateProcess 方法嘗試在應用程式容器之外啟動可執行檔，則會發生錯誤。  
  
 除非您使用 [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 選項指定輸出檔名稱，否則將會以包含 [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) 方法的輸入檔名稱命名。  
  
 如果您在命令提示字元指定這個選項，直到下一個 **\/out** 或 **\/target** 選項之前所有的檔案都會用來建立可執行檔。  
  
### 若要在 IDE 中設定這個編譯器選項  
  
1.  在 \[**方案總管**\] 中，開啟專案的捷徑功能表，然後選擇 \[**屬性**\]。  
  
2.  在 \[**應用程式**\] 索引標籤上，選擇 \[**輸出類型**\] 清單中的 \[**Windows 市集應用程式**\]。  
  
     這個選項只適用於 [!INCLUDE[win8_appname_long](../../../csharp/includes/win8-appname-long-md.md)]應用程式範本。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## 範例  
 下列命令會將 `filename.cs` 編譯至一個只能在應用程式容器中執行的 Windows 可執行檔。  
  
```  
csc /target:appcontainerexe filename.cs  
```  
  
## 請參閱  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [\/target:winexe \(Create a Windows Program\)](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)