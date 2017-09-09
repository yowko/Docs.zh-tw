---
title: "/keyfile (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/keyfile"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/keyfile compiler option [C#]"
  - "-keyfile compiler option [C#]"
  - "keyfile compiler option [C#]"
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# /keyfile (C# Compiler Options)
指定包含密碼編譯金鑰的檔名。  
  
## 語法  
  
```  
/keyfile:file  
```  
  
## 引數  
  
|詞彙|定義|  
|--------|--------|  
|`file`|含有強式名稱金鑰的檔案名稱|  
  
## 備註  
 當使用這個選項時，編譯器會從指定檔案將公開金鑰插入組件資訊清單，然後使用私密金鑰簽署最終組件。  若要產生金鑰檔，請在命令列中輸入 sn \-k `file`。  
  
 如果您使用 **\/target:module** 進行編譯，該金鑰檔的名稱便會儲存在模組中，並會合併至使用 [\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) 編譯組件時所建立的組件。  
  
 您也可以使用 [\/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md) 將加密資訊傳遞至編譯器，  如果您想要部分簽署的組件，請使用 [\/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)。  
  
 若在相同的編譯器中指定 \/keyfile 和 \/keycontainer \(不論是以命令列選項或是自訂屬性的方式\)，編譯器會先試用金鑰容器。  如果這個動作成功，那麼組件就會使用金鑰容器中的資訊加以簽署。  如果編譯器找不到金鑰容器，則會試用 \/keyfile 指定的檔案。  如果此動作成功，組件會以金鑰檔內的資訊簽署，並將金鑰資訊安裝於金鑰容器內 \(類似於 sn \-i\)，以便在下次編譯時，讓金鑰容器有效。  
  
 請注意，金鑰檔可能只包含公開金鑰。  
  
 如需詳細資訊，請參閱[建立和使用強式名稱的組件](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)以及[延遲簽署組件](../Topic/Delay%20Signing%20an%20Assembly.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**簽署**\] 屬性頁。  
  
3.  修改 \[**選擇強式名稱金鑰檔**\] 屬性。  
  
 您可以使用 <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>，以程式設計方式存取這個編譯器選項。  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)