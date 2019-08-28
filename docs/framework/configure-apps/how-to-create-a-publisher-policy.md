---
title: 作法：建立發行者原則
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 16d11147af7b54d492c099269a48a92ce83bc05d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044003"
---
# <a name="how-to-create-a-publisher-policy"></a>作法：建立發行者原則

元件的廠商可以指出應用程式應該使用較新版本的元件, 方法是包含發行者原則檔案與已升級的元件。 發行者原則檔會指定元件重新導向和程式碼基底設定, 並使用與應用程式佈建檔相同的格式。 發行者原則檔會編譯成元件, 並放在全域組件快取中。

建立發行者原則包含三個步驟:

1. 建立發行者原則檔。

2. 建立發行者原則元件。

3. 將發行者原則元件加入至全域組件快取。

重新導向[元件版本](redirect-assembly-versions.md)中會描述發行者原則的架構。 下列範例顯示將某個版本重新導向至另一個版本的`myAssembly`發行者原則檔。

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

若要瞭解如何指定程式碼基底, 請參閱[指定元件的位置](specify-assembly-location.md)。

## <a name="creating-the-publisher-policy-assembly"></a>建立發行者原則元件

使用[元件連結器 (al.exe)](../tools/al-exe-assembly-linker.md)來建立發行者原則元件。

#### <a name="to-create-a-publisher-policy-assembly"></a>若要建立發行者原則元件

1. 在命令提示字元中輸入下列命令:

    **al/link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*

    在此命令中:

    - *PublisherPolicyFile*引數是發行者原則檔的名稱。

    - *PublisherPolicyAssemblyFile*引數是此命令所產生之發行者原則元件的名稱。 元件檔案名的格式必須如下:

      **策略.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**

    - *KeyPairFile*引數是包含金鑰組的檔案名。 您必須使用相同的金鑰組來簽署元件和發行者原則元件。

    - *ProcessorArchitecture*引數會識別特定處理器元件的目標平臺。

      > [!NOTE]
      > 以特定處理器架構為目標的能力是 .NET Framework 版本2.0 中的新功能。

    下列命令會從名`policy.1.0.myAssembly` `pub.config`為的發行者原則檔案建立名為的發行者原則元件, 並使用檔案中`sgKey.snk`的金鑰組將強式名稱指派給元件, 並指定元件以 x86 為目標處理器架構。

    ```
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
    ```

    發行者原則元件必須符合其適用之元件的處理器架構。 因此, 如果您的元件具有<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A>的<xref:System.Reflection.ProcessorArchitecture.MSIL>值, 則必須使用`/platform:anycpu`來建立該元件的發行者原則元件。 您必須為每個處理器特定的元件提供個別的發行者原則元件。

    這項規則的結果是, 若要變更元件的處理器架構, 您必須變更版本號碼的主要或次要元件, 讓您可以使用正確的處理器架構來提供新的發行者原則元件。 當您的元件有不同的處理器架構時, 舊的發行者原則元件無法服務您的元件。

    另一個結果是版本2.0 連結器無法用來建立使用舊版 .NET Framework 所編譯之元件的發行者原則元件, 因為它一律會指定處理器架構。

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>將發行者原則元件加入至全域組件快取

使用[全域組件快取工具 (Gacutil)](../tools/gacutil-exe-gac-tool.md) , 將發行者原則元件加入至全域組件快取。

#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>將發行者原則元件加入至全域組件快取

1. 在命令提示字元中輸入下列命令:

    **gacutil/i**  *publisherPolicyAssemblyFile*

    下列命令會將`policy.1.0.myAssembly.dll`新增至全域組件快取。

    ```
    gacutil /i policy.1.0.myAssembly.dll
    ```

    > [!IMPORTANT]
    > 發行者原則元件無法加入至全域組件快取, 除非原始發行者原則檔位於與元件相同的目錄中。

## <a name="see-also"></a>另請參閱

- [使用組件設計程式](../app-domains/programming-with-assemblies.md)
- [執行階段如何找出組件](../deployment/how-the-runtime-locates-assemblies.md)
- [使用設定檔設定應用程式](index.md)
- [執行階段設定結構描述](./file-schema/runtime/index.md)
- [組態檔結構描述](./file-schema/index.md)
- [重新導向組件版本](redirect-assembly-versions.md)
