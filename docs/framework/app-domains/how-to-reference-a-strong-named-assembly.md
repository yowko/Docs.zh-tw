---
title: "如何：參考強式名稱簽署組件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "組件 [.NET Framework], 強式命名"
  - "組件繫結, 強式命名"
  - "編譯時期組件參考"
  - "強式名稱組件, 編譯時期參考"
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：參考強式名稱簽署組件
參考強式名稱組件的型別或資源的處理序 \(Process\) 通常是透明的。  您可以在編譯期間 \(早期繫結\) 或執行階段進行參考。  
  
 當您向編譯器指出您的組件明確參考其他組件時，便會發生編譯期間參考。  使用編譯期間參考時，編譯器會自動取得目標強式名稱組件的公開金鑰，並將該金鑰放入正在進行編譯之組件的組件參考中。  
  
> [!NOTE]
>  強式名稱組件只能使用來自其他強式名稱組件的型別。  否則，此強式名稱組件的安全性將受到威脅。  
  
### 若要對強式名稱的組件進行編譯期間參考  
  
1.  在命令提示字元中輸入下列命令：  
  
     \<*compiler command*\> **\/reference:**\<*assembly name*\>  
  
     在這個命令中，*compiler command* 是您使用的語言的編譯器命令，而*assembly name* 則為被參考的強式名稱組件的名稱。  您也可以使用其他編譯器選項，例如 **\/t:library** 選項，來建立程式庫組件。  
  
 下列範例建立 `myAssembly.dll` 組件，它參考來自 `myAssembly.cs` 程式庫模組的 `myLibAssembly.dll` 強式名稱組件。  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### 若要對強式名稱的組件進行執行階段參考  
  
1.  當您對強式名稱組件進行執行階段參考 \(例如使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 或 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName> 方法\) 時，必須使用所參考強式名稱組件的顯示名稱。  顯示名稱的語法如下：  
  
     \<*assembly name*\>**,** \<*version number*\>**,** \<*culture*\>**,** \<*public key token*\>  
  
     例如：  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     在這個範例中，`PublicKeyToken` 是十六進位格式的公開金鑰語彙基元。  如果沒有文化特性值，則使用 `Culture=neutral`。  
  
 下列程式碼範例說明如何使用這項資訊和 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法。  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 您可以使用下列[強式名稱 \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) 命令來列印特定組件的十六進位格式公開金鑰和公開金鑰語彙基元：  
  
 **sn \-Tp \<** *assembly* **\>**  
  
 如果您擁有公開金鑰檔，則可以使用下列命令 \(請注意命令列選項的大小寫不同處\)：  
  
 **sn \-tp \<** *assembly* **\>**  
  
## 請參閱  
 [建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)