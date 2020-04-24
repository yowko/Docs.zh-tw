---
title: 如何：建立發行者原則
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646062"
---
# <a name="how-to-create-a-publisher-policy"></a>如何：建立發行者原則

程式集的供應商可以聲明應用程式應使用較新版本的程式集,通過將發佈者策略檔與升級的程式集一起。 發行者策略檔指定程式集重定向和代碼庫設置,並使用與應用程式設定檔相同的格式。 發行者策略檔編譯到程式集中並放置在全域程式集緩存中。

建立發行者政策涉及三個步驟:

1. 建立發行者策略檔。

2. 建立發行者策略程式集。

3. 將發行者策略程式集添加到全域程式集緩存。

發行者策略的架構在[重定向程式集版本](redirect-assembly-versions.md)中描述。 下面的範例顯示一個發行者策略檔,該檔將一`myAssembly`個版本重定向到另一個版本。

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

要瞭解如何指定程式庫,請參閱[指定程式集的位置](specify-assembly-location.md)。

## <a name="creating-the-publisher-policy-assembly"></a>建立發行者原則程式集

使用[程式集連結器 (Al.exe)](../tools/al-exe-assembly-linker.md)建立發行者策略程式集。

#### <a name="to-create-a-publisher-policy-assembly"></a>建立發行者原則程式集

在命令提示字元中輸入下列命令：

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

在這個命令中：

- 參數`publisherPolicyFile`是發布者策略檔的名稱。

- 該`publisherPolicyAssemblyFile`參數是此命令產生的發行者策略程式集的名稱。 程式集檔名稱必須遵循以下格式:

  "策略.主要編號.次要編號.mainAssemblyname.dll"

- 參數`keyPairFile`是包含金鑰對的檔的名稱。 您必須使用相同的金鑰對對程式集和發行者策略程式集進行簽名。

- 參數`processorArchitecture`標識處理器特定程式集的目標平臺。

  > [!NOTE]
  > 從 .NET 框架 2.0 開始,可以定位特定處理器體系結構。

從 .NET 框架 2.0 開始,可以定位特定處理器體系結構。 以下命令創建一個發佈者策略程式集`policy.1.0.myAssembly`,該程式集從稱為`pub.config`的 發行者策略檔調用`sgKey.snk`,使用 檔中的密鑰對向程式集分配強名稱,並指定程式集以 x86 處理器體系結構為目標。

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

發行者策略程式集必須與它所應用的程式集的處理器體系結構匹配。 因此,如果程式集的值<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A>為<xref:System.Reflection.ProcessorArchitecture.MSIL>`/platform:anycpu` 您必須為每個特定於處理器的程式集提供單獨的發行者策略程式集。

此規則的結果是,為了更改程式集的處理器體系結構,必須更改版本號的主要或次要元件,以便可以使用正確的處理器體系結構提供新的發行者策略程式集。 一旦程式集具有不同的處理器體系結構,舊的發行者策略程式集將無法為程式集提供服務。

另一個後果是,版本 2.0 連結器不能用於為使用早期版本的 .NET Framework 編譯的程式集創建發行者策略程式集,因為它始終指定處理器體系結構。

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>將宣告者政策程式集到全域程式集快取

使用[全域程式集快取工具 (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md)將發布者策略程式集添加到全域程式集緩存。

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>將宣告者政策程式集到全域程式集快取

在命令提示字元中輸入下列命令：

```console
gacutil /i publisherPolicyAssemblyFile
```

以下命令添加到`policy.1.0.myAssembly.dll`全域程式集緩存。

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> 除非`/link`參數中指定的原始發行者策略檔與程式集位於同一目錄中,否則無法將發行者策略程式集添加到全域程式集緩存中。

## <a name="see-also"></a>另請參閱

- [使用組件設計程式](../../standard/assembly/index.md)
- [執行階段如何找出組件](../deployment/how-the-runtime-locates-assemblies.md)
- [使用組態檔設定應用程式](index.md)
- [執行時設定架構](./file-schema/runtime/index.md)
- [設定檔案架構](./file-schema/index.md)
- [重新導向組件版本](redirect-assembly-versions.md)
