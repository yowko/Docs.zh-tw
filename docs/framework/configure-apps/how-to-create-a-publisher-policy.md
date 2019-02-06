---
title: HOW TO：建立發行者原則
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: b98d3ef62fc9dda48920d32fed6f6acf797334d6
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758985"
---
# <a name="how-to-create-a-publisher-policy"></a>HOW TO：建立發行者原則
組件的廠商可以應用程式應該使用較新版的組件，包含與升級後的組件的發行者原則檔的狀態。 發行者原則檔會指定組件重新導向和程式碼基底設定，並使用應用程式組態檔相同的格式。 發行者原則檔會編譯成組件，並放置於全域組件快取。  
  
 建立發行者原則是三個步驟：  
  
1.  建立發行者原則檔。  
  
2.  建立發行者原則組件。  
  
3.  將發行者原則組件新增至全域組件快取中。  
  
 發行者原則的結構描述所述[重新導向組件版本](../../../docs/framework/configure-apps/redirect-assembly-versions.md)。 下列範例顯示發行者原則檔會將重新導向的一個版本`myAssembly`到另一個。  
  
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
  
 若要了解如何指定程式碼基底，請參閱[指定組件的位置](../../../docs/framework/configure-apps/specify-assembly-location.md)。  
  
## <a name="creating-the-publisher-policy-assembly"></a>建立發行者原則組件  
 使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md)建立發行者原則組件。  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>若要建立發行者原則組件  
  
1.  在命令提示字元中輸入下列命令：  
  
     **al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*  
  
     在這個命令：  
  
    -   *PublisherPolicyFile*引數是發行者原則檔的名稱。  
  
    -   *PublisherPolicyAssemblyFile*引數是此命令會產生發行者原則組件的名稱。 組件檔案名稱必須遵循格式：  
  
         **原則。** *majorNumber* **。** *minorNumber* **。** *mainAssemblyName* **.dll**  
  
    -   *KeyPairFile*引數是含有金鑰組檔案的名稱。 您必須簽署的組件和相同的金鑰組的發行者原則組件。  
  
    -   *ProcessorArchitecture*引數會識別特定處理器的組件的目標平台。  
  
        > [!NOTE]
        >  能夠針對特定的處理器架構是.NET Framework 2.0 版中的新功能。  
  
     下列命令會建立稱為發行者原則組件`policy.1.0.myAssembly`從發行者原則檔名`pub.config`，將強式名稱指派給使用中的金鑰組的組件`sgKey.snk`檔案，並指定組件以 x86 為目標處理器架構。  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     發行者原則組件必須符合的組件，它會套用到的處理器架構。 因此，如果您的組件<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A>的值<xref:System.Reflection.ProcessorArchitecture.MSIL>，必須使用建立發行者原則組件，該組件`/platform:anycpu`。 您必須提供個別針對每個處理器特定組件的發行者原則組件。  
  
     此規則的結果是，若要變更組件的處理器架構，您必須變更的主要或次要的元件的版本號碼，以便您可以提供新的發行者原則組件，以正確的處理器架構。 一旦您的組件具有不同的處理器架構，將舊的發行者原則組件無法服務您的組件。  
  
     另一種結果是 2.0 版連結器，不能用來建立編譯使用舊版.NET Framework 中，因為它一律會指定處理器架構的組件的發行者原則組件。  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>將發行者原則組件新增至全域組件快取  
 使用[全域組件快取工具 (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)將發行者原則組件新增至全域組件快取。  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>將發行者原則組件新增至全域組件快取  
  
1.  在命令提示字元中輸入下列命令：  
  
     **gacutil /i**  *publisherPolicyAssemblyFile*  
  
     下列命令會將`policy.1.0.myAssembly.dll`至全域組件快取。  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  發行者原則組件無法新增至全域組件快取，除非原始發行者原則檔位於與組件相同的目錄中。  
  
## <a name="see-also"></a>另請參閱
- [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [使用組態檔設定應用程式](../../../docs/framework/configure-apps/index.md)
- [執行階段設定結構描述](../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)
- [重新導向組件版本](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
