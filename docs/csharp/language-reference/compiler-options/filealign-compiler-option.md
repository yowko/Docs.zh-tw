---
title: "/filealign (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/filealign"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/alignment compiler option [C#]"
  - "filealign compiler option [C#]"
  - "-filealign compiler option [C#]"
  - "/sections compiler option [C#]"
  - "alignment compiler option [C#]"
  - "sections compiler option [C#]"
  - "-sections compiler option [C#]"
  - "/filealign compiler option [C#]"
  - "file sharing [C#]"
  - "-alignment compiler option [C#]"
  - "section alignment [C#]"
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# /filealign (C# Compiler Options)
**\/filealign** 選項讓您可以指定輸出檔的區段大小。  
  
## 語法  
  
```  
/filealign:number  
```  
  
## 引數  
 `number`  
 指定輸出檔中區段大小的值，  有效值為 512、1024、2048、4096 和 8192。  這些值是以位元組為單位。  
  
## 備註  
 每個區段會對齊於 **\/filealign** 值倍數的界限，  沒有固定預設值。  如果沒有指定 **\/filealign**，Common Language Runtime 會在編譯時期選取一個預設值。  
  
 您可藉由指定區段大小來影響輸出檔的大小，  修改區段大小對將執行於較小裝置上的程式很有幫助。  
  
 請使用 [DUMPBIN](/visual-cpp/build/reference/dumpbin-options) 來檢視輸出檔中區段的相關資訊。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**建置**\] 屬性頁。  
  
3.  按一下 \[**進階**\] 按鈕。  
  
4.  修改 \[**檔案對齊**\] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>。  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)