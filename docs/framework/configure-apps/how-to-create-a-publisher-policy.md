---
title: 如何：建立發行者原則
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 91971e4d41c3a54fa72ae73a3655dab650019676
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758122"
---
# <a name="how-to-create-a-publisher-policy"></a>如何：建立發行者原則
組件的廠商可以狀態的應用程式應該使用較新版的組件，包含與升級後的組件的發行者原則檔。 發行者原則檔會指定組件重新導向和程式碼基底的設定，並使用相同的格式為應用程式組態檔。 發行者原則檔會編譯的組件，並放置於全域組件快取。  
  
 建立發行者原則是三個步驟：  
  
1.  建立發行者原則檔。  
  
2.  建立發行者原則組件。  
  
3.  將發行者原則組件加入至全域組件快取。  
  
 發行者原則的結構描述所述[重新導向組件版本](../../../docs/framework/configure-apps/redirect-assembly-versions.md)。 下列範例顯示發行者原則檔重新導向的一個版本`myAssembly`到另一個。  
  
```xml  
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
  
 若要深入了解如何指定程式碼基底，請參閱[指定組件的位置](../../../docs/framework/configure-apps/specify-assembly-location.md)。  
  
## <a name="creating-the-publisher-policy-assembly"></a>建立發行者原則組件  
 使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md)建立發行者原則組件。  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>若要建立發行者原則組件  
  
1.  在命令提示字元中輸入下列命令：  
  
     **al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*  
  
     在這個命令：  
  
    -   *PublisherPolicyFile*引數是發行者原則檔名稱。  
  
    -   *PublisherPolicyAssemblyFile*引數是此命令會產生發行者原則組件名稱。 組件檔案名稱必須遵循格式：  
  
         **原則。** *majorNumber* **。** *minorNumber* **。** *mainAssemblyName* **.dll**  
  
    -   *KeyPairFile*引數是包含金鑰組的檔案名稱。 您必須簽署的組件和發行者原則組件具有相同的金鑰組。  
  
    -   *ProcessorArchitecture*引數會識別特定處理器的組件的目標平台。  
  
        > [!NOTE]
        >  特定處理器架構為目標的能力是在.NET Framework 2.0 版的新功能。  
  
     下列命令會建立稱為發行者原則組件`policy.1.0.myAssembly`從發行者原則檔呼叫`pub.config`，將強式名稱指派給使用中的金鑰組的組件`sgKey.snk`檔案，並指定組件以 x86 為目標處理器架構。  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     發行者原則組件必須符合它所適用的組件的處理器架構。 因此，如果您的組件<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A>值<xref:System.Reflection.ProcessorArchitecture.MSIL>，您必須以建立發行者原則組件，該組件`/platform:anycpu`。 您必須提供不同的每個處理器特定組件的發行者原則組件。  
  
     此規則的結果是，若要變更之組件的處理器架構，您必須變更主要或次要的元件版本號碼，這麼做，您可以提供新的發行者原則組件，以正確的處理器架構。 一旦您的組件具有不同的處理器架構，舊的發行者原則組件無法服務您的組件。  
  
     另一種結果是 2.0 版連結器無法用於建立編譯使用舊版.NET Framework 中，因為它一律指定處理器架構的組件的發行者原則組件。  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>將發行者原則組件加入至全域組件快取  
 使用[全域組件快取工具 (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)將發行者原則組件新增至全域組件快取。  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>將發行者原則組件新增至全域組件快取  
  
1.  在命令提示字元中輸入下列命令：  
  
     **gacutil /i***publisherPolicyAssemblyFile*   
  
     下列命令會將`policy.1.0.myAssembly.dll`至全域組件快取。  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  發行者原則組件無法新增至全域組件快取，除非原始發行者原則檔位於與組件相同的目錄中。  
  
## <a name="see-also"></a>另請參閱  
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [設定應用程式](../../../docs/framework/configure-apps/index.md)  
 [設定.NET Framework 應用程式](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [執行階段設定結構描述](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)  
 [重新導向組件版本](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
