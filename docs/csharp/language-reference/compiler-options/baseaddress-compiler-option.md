---
title: "/baseaddress (C# Compiler Options) | Microsoft Docs"
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
  - "/dllbase"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "baseaddress compiler option [C#]"
  - "/baseaddress compiler option [C#]"
  - "-baseaddress compiler option [C#]"
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /baseaddress (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/baseaddress** 選項可讓您指定載入 DLL 的慣用基底位址 \(Base Address\)。  如需這個選項使用時機與使用原因的詳細資訊，請參閱 [增進應用程式的啟動時間。](http://go.microsoft.com/fwlink/?LinkId=107043) 和 [Larry Osterman 的網誌](http://go.microsoft.com/fwlink/?LinkId=107044)。  
  
## 語法  
  
```  
/baseaddress:address  
```  
  
## Arguments  
 `address`  
 DLL 的基底位址。  這個位址可指定為十進位、十六進位或八進位。  
  
## 備註  
 DLL 的預設基底位址是由 .NET Framework Common Language Runtime 設定。  
  
 請注意，位址中低序位字元組 \(Low\-Order Word\) 會捨去。  例如，如果您指定的是 0x11110001，就會調整為 0x11110000。  
  
 若要完成 DLL 的簽署程序，可以使用 SN.EXE 搭配 \-R 選項。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**建置**\] 屬性頁。  
  
3.  按一下 \[進階\] 按鈕。  
  
4.  修改 \[**DLL 基底位址**\] 屬性。  
  
     若要用程式設計的方式設定這個編譯器選項，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>。  
  
## 請參閱  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=fullName>   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)