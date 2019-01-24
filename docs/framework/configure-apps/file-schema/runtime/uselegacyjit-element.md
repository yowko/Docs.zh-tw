---
title: '&lt;Uselegacyjit>&gt;項目'
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecf4d805feeb27a7c3fa08d2ab6dd05b6fff693a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648176"
---
# <a name="ltuselegacyjitgt-element"></a>&lt;Uselegacyjit>&gt;項目

決定通用語言執行平台是否針對 Just-In-Time 編譯使用舊版 64 位元 JIT 編譯器。  
  
\<configuration>  
\<執行階段 >  
\<useLegacyJit>
  
## <a name="syntax"></a>語法  
  
```xml
<useLegacyJit enabled=0|1 />
```

項目名稱`useLegacyJit`會區分大小寫。
  
## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
| 屬性 | 描述                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | 必要屬性。<br><br>指定執行階段是否使用舊版 64 位元 JIT 編譯器。 |  
  
### <a name="enabled-attribute"></a>啟用的屬性  
  
| 值 | 描述                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | Common language runtime 會使用.NET Framework 4.6 和更新版本中所包含的新 64 位元 JIT 編譯器。 |  
| 1     | Common language runtime 會使用舊版 64 位元 JIT 編譯器。                                                     |  
  
### <a name="child-elements"></a>子元素

無
  
### <a name="parent-elements"></a>父元素  
  
| 元素         | 描述                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |  
| `runtime`       | 包含有關執行階段初始化選項的資訊。                                                        |  
  
## <a name="remarks"></a>備註  

從.NET Framework 4.6 開始，common language runtime 預設會使用新的 64 位元編譯器進行 Just-In-Time (JIT) 編譯。 在某些情況下，這可能會導致從應用程式是由舊版 64 位元 JIT 編譯器的 JIT 編譯的程式碼的行為差異。 藉由設定`enabled`的屬性`<useLegacyJit>`項目`1`，您可以停用新的 64 位元 JIT 編譯器，並改為編譯您的應用程式使用舊版 64 位元 JIT 編譯器。  
  
> [!NOTE]
> `<useLegacyJit>`項目會影響僅 64 位元 JIT 編譯。 使用 32 位元 JIT 編譯器的編譯不受影響。  
  
而不是使用組態檔設定，您可以啟用舊版 64 位元 JIT 編譯器，另外兩種方式：  
  
- 設定環境變數

  設定`COMPLUS_useLegacyJit`環境變數設為`0`（使用新的 64 位元 JIT 編譯器） 或`1`（使用舊版 64 位元 JIT 編譯器）：
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  環境變數*全域範圍*，也就是說，它會影響所有應用程式的電腦上執行。 如果設定，它會覆寫應用程式組態檔的設定。 環境變數名稱不區分大小寫。
  
- 新增登錄機碼

  您可以藉由新增啟用舊版 64 位元 JIT 編譯器`REG_DWORD`值設為`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework`或`HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`金鑰在登錄中。 值為`useLegacyJit`。 如果值為 0，則會使用新的編譯器。 如果值為 1，則會啟用舊版 64 位元 JIT 編譯器。 登錄值名稱不區分大小寫。
  
  值來加入`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework`金鑰會影響電腦上執行的所有應用程式。 值來加入`HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`金鑰會影響目前使用者所執行的所有應用程式。 如果機器已使用多個使用者帳戶，只有目前使用者所執行的應用程式會受到影響，除非此值會加入至其他使用者的登錄機碼。 新增`<useLegacyJit>`組態檔的項目覆寫登錄設定中，如果它們存在。  
  
## <a name="example"></a>範例  

下列組態檔會停用新的 64 位元 JIT 編譯器的編譯，並改為使用舊版 64 位元 JIT 編譯器。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [\<執行階段 > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)
- [\<configuration> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
- [風險降低：新的 64 位元 JIT 編譯器](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
