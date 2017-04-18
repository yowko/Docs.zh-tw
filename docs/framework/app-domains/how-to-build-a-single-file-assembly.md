---
title: "如何：建置單一檔案組件 | Microsoft Docs"
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
  - "組件 [.NET Framework], 單一檔案"
  - "組件資訊清單, 單一檔案組件"
  - "程式碼模組"
  - "命令列編譯器"
  - "程式庫組件"
  - "組件的輸出檔名"
  - "單一檔案組件"
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：建置單一檔案組件
單一檔案組件為最簡單的組件型別，含有型別資訊和實作 \(Implementation\) 和[組件資訊清單](../../../docs/framework/app-domains/assembly-manifest.md)。  您可以使用命令列編譯器或 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 來建立單一檔案組件。  根據預設，編譯器會建立具有 .exe 副檔名的組件檔案。  
  
> [!NOTE]
>  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for C\# 和 Visual Basic 只能用來建立單一檔案組件。  如果您想建立多檔案的組件，必須使用命令列編譯器或 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C\+\+。  
  
 下列程序將說明如何使用命令列編譯器來建立單一檔案組件。  
  
### 若要建立具有 .exe 副檔名的組件  
  
1.  在命令提示字元中輸入下列命令：  
  
     \<*compiler command*\> \<*module name*\>  
  
     在這個命令中，*compiler command* 是您程式碼模組中使用的語言編譯器命令，而 *module name* 則是編譯到組件的程式碼模組名稱。  
  
 下列範例會從名為 `myCode` 的程式碼模組，建立名為 `myCode.exe` 的組件。  
  
```csharp  
csc myCode.cs  
```  
  
```vb  
vbc myCode.vb  
```  
  
#### 若要建立副檔名為 .exe 的組件並指定輸出檔名  
  
1.  在命令提示字元中輸入下列命令：  
  
     \<*compiler command*\> **\/out:**\<*file name*\> \<*module name*\>  
  
     在這個命令中，*compiler command* 是您程式碼模組中使用的語言編譯器命令、*file name* 是輸出檔名，而 *module name* 則是編譯到組件的程式碼模組名稱。  
  
 下列範例會從名稱為 `myCode` 的程式碼模組，建立命名為 `myAssembly.exe` 組件。  
  
```csharp  
csc /out:myAssembly.exe myCode.cs  
```  
  
```vb  
vbc /out:myAssembly.exe myCode.vb  
```  
  
## 建立程式庫組件  
 程式庫組件與類別庫相似。  它含有供其他組件參考的型別，但沒有可開始執行的進入點。  
  
#### 若要建立程式庫組件  
  
1.  在命令提示字元中輸入下列命令：  
  
     \<*compiler command*\> **\/t:library** \<*module name*\>  
  
     在這個命令中，*compiler command* 是您程式碼模組中使用的語言編譯器命令，而 *module name* 則是編譯到組件的程式碼模組名稱。  您也可以使用其他的編譯器選項，例如 **\/out:** 選項。  
  
 下列範例從 `myCode` 程式庫模組建立 `myCodeAssembly.dll` 程式庫組件。  
  
```csharp  
csc /out:myCodeLibrary.dll /t:library myCode.cs  
```  
  
```vb  
vbc /out:myCodeLibrary.dll /t:library myCode.vb  
```  
  
## 請參閱  
 [建立組件](../../../docs/framework/app-domains/create-assemblies.md)   
 [多檔案組件](../../../docs/framework/app-domains/multifile-assemblies.md)   
 [如何：建置多檔案組件](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)   
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)