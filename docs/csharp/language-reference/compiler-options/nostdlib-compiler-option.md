---
title: "/nostdlib (C# Compiler Options) | Microsoft Docs"
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
  - "/nostdlib"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "nostdlib compiler option [C#]"
  - "-nostdlib compiler option [C#]"
  - "/nostdlib compiler option [C#]"
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /nostdlib (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/nostdlib** 會導致無法匯入 mscorlib.dll，它定義了整個系統命名空間。  
  
## 語法  
  
```  
/nostdlib[+ | -]  
```  
  
## 備註  
 如果您想要定義或建立自己的系統命名空間和物件，請使用此選項。  
  
 如果您未指定 **\/nostdlib**，mscorlib.dll 會匯入到您的程式 \(與指定 **\/nostdlib\-** 相容\)。 指定 **\/nostdlib** 等同於指定 **\/nostdlib\+**。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[屬性\] 頁面。  
  
2.  按一下 \[建置\] 屬性頁面。  
  
3.  按一下 \[**進階**\] 按鈕。  
  
4.  修改 \[不要參考 mscorlib.dll\] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>。  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)