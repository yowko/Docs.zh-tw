---
title: "如何：建立發行者原則 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GAC (全域組件快取), 發行者原則組件"
  - "全域組件快取, 發行者原則組件"
  - "發行者原則組件"
  - "發行者原則檔"
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# 如何：建立發行者原則
組件製造商可以藉著將發行者原則檔和升級的組件包含在一起，來聲明應用程式應該使用組件的較新版本。  發行者原則檔會指定組件重新導向和程式碼基底 \(Code Base\) 設定，並使用和應用程式組態檔相同的格式。  發行者原則檔會編譯到組件中，並且放在全域組件快取中。  
  
 建立發行者原則包括三個步驟：  
  
1.  建立發行者原則檔。  
  
2.  建立發行者原則組件。  
  
3.  將發行者原則組件加入至全域組件快取中。  
  
 發行者原則的結構描述是在[重新導向組件版本](../../../docs/framework/configure-apps/redirect-assembly-versions.md)中描述。  下列範例說明將 `myAssembly` 的一個版本重新導向另一個版本的發行者原則檔。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->  
         <bindingRedirect oldVersion="1.0.0.0"  
                          newVersion="2.0.0.0"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 若要暸解如何指定程式碼基底，請參閱[指定組件的位置](../../../docs/framework/configure-apps/specify-assembly-location.md)。  
  
## 建立發行者原則組件  
 請使用[組件連結器 \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) 來建立發行者原則組件。  
  
#### 若要建立發行者原則組件  
  
1.  在命令提示字元中輸入下列命令：  
  
     **al \/link:** *publisherPolicyFile* **\/out:** *publisherPolicyAssemblyFile* **\/keyfile:** *keyPairFile* **\/platform:** *processorArchitecture*  
  
     在這個命令中：  
  
    -   *publisherPolicyFile* 引數是指發行者原則檔的名稱。  
  
    -   *publisherPolicyAssemblyFile* 引數是指由這個命令所產生的發行者原則組件名稱。  組件的檔名必須遵循下列格式：  
  
         **policy.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    -   *keyPairFile* 引數是指包含金鑰組 \(Key Pair\) 的檔案名稱。  您必須用相同的金鑰組簽署組件和發行者原則組件。  
  
    -   *processorArchitecture* 引數會識別特定處理器組件的目標平台，  
  
        > [!NOTE]
        >  將特定處理器架構設定為目標的功能是 .NET Framework 2.0 版的新增功能。  
  
     下列命令會從發行者原則檔 `pub.config` 建立命名為 `policy.1.0.myAssembly` 的發行者原則組件、使用 `sgKey.snk` 檔中的金鑰組 \(Key Pair\)，為此組件指派強式名稱 \(Strong Name\)，以及將此組件的目標指定為 x86 處理器架構。  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     發行者原則組件必須符合它所適用之組件的處理器架構；  因此，如果您的組件具有 <xref:System.Reflection.ProcessorArchitecture> 的 <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> 值，則必須以 `/platform:anycpu` 建立該組件的發行者原則組件。  您必須針對每個處理器特有組件提供個別的發行者原則組件。  
  
     這個規則的結果如下：為了變更組件的處理器架構，您必須變更主要版本號碼和次要版本號碼，以便能夠為新的發行者原則組件提供正確的處理器架構。  一旦您的組件使用不同的處理器架構時，舊的發行者原則組件便無法為您的組件提供服務。  
  
     另一種結果是 2.0 版連結器 \(Linker\) 無法用來針對使用舊版 .NET Framework 所編譯的組件建立發行者原則組件，因為該組件一定會指定處理器架構。  
  
## 將發行者原則組件加入至全域組件快取中  
 請使用[全域組件快取工具 \(Gacutil.exe\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 將發行者原則組件加入至全域組件快取中。  
  
#### 若要將發行者原則組件加入至全域組件快取中  
  
1.  在命令提示字元中輸入下列命令：  
  
     **gacutil \/i**  *publisherPolicyAssemblyFile*  
  
     下列命令會將 `policy.1.0.myAssembly.dll` 加入至全域組件快取中。  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  除非原始的發行者原則檔與發行者原則組件位於相同目錄，否則無法將這個組件加入至全域組件快取中。  
  
## 請參閱  
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)   
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [設定應用程式](../../../docs/framework/configure-apps/index.md)   
 [Configuring .NET Framework Apps](http://msdn.microsoft.com/zh-tw/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)   
 [執行階段設定結構描述](../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)   
 [重新導向組件版本](../../../docs/framework/configure-apps/redirect-assembly-versions.md)