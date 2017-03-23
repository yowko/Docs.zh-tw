---
title: "/langversion (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/langversion"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/langversion compiler option [C#]"
  - "-langversion compiler option [C#]"
  - "langversion compiler option [C#]"
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
caps.latest.revision: 33
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 33
---
# /langversion (C# Compiler Options)
讓編譯器只能接受選擇之 C\# 語言規格中所包含的語法。  
  
## 語法  
  
```  
/langversion:option  
```  
  
## Arguments  
 `option`  
 下列是有效值：  
  
|選項|意義|  
|--------|--------|  
|default|編譯器會接受所有有效的語言語法。|  
|ISO\-1|編譯器只會接受內含在 ISO\/IEC 23270:2003 C\# 語言規格中的語法。|  
|ISO\-2|編譯器只會接受內含在 ISO\/IEC 23270:2006 C\# 語言規格中的語法。  此規格可於 [ISO](http://go.microsoft.com/fwlink/?LinkId=144406) 網站上找到。|  
|3|編譯器只會接受包含在 [C\# 語言規格](../../../csharp/language-reference/language-specification.md) 3.0 版中的語法。|  
  
## 備註  
 C\# 應用程式參考的中繼資料 \(Metadata\) 不受 **\/langversion** 編譯器選項的控制。  
  
 由於每個版本的 C\# 編譯器都包含語言規格的擴充部分，因此 **\/langversion** 不會提供您舊版編譯器的相同功能。  
  
 無論您使用那個 **\/langversion** 設定，都將使用目前的 Common Language Runtime 版本建立 .exe 或 .dll。  friend 組件和 [\/moduleassemblyname \(Specify Friend Assembly for Module\)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) 是例外，這兩者會在 **\/langversion:ISO\-1** 下工作。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**建置**\] 屬性頁。  
  
3.  按一下 \[進階\] 按鈕。  
  
4.  修改 \[**語言版本**\] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>。  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [C\# 語言規格](../../../csharp/language-reference/language-specification.md)