---
title: <useLegacyJit> 項目
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
ms.openlocfilehash: 47aacb629dc234d9aeaab1ef6e6844fbbe5dbfdb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115100"
---
# <a name="uselegacyjit-element"></a>\<useLegacyJit> 項目

決定通用語言執行平台是否針對 Just-In-Time 編譯使用舊版 64 位元 JIT 編譯器。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<uselegacyjit> >**  
  
## <a name="syntax"></a>語法  
  
```xml
<useLegacyJit enabled=0|1 />
```

元素名稱 `useLegacyJit` 區分大小寫。
  
## <a name="attributes-and-elements"></a>屬性和元素

下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
| 屬性 | 描述                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | 必要屬性。<br><br>指定執行時間是否使用舊版64位 JIT 編譯程式。 |  
  
### <a name="enabled-attribute"></a>enabled 屬性  
  
| 值 | 描述                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | 通用語言執行時間會使用 .NET Framework 4.6 和更新版本中所包含的新64位 JIT 編譯程式。 |  
| 1     | 通用語言執行時間會使用舊版的64位 JIT 編譯程式。                                                     |  
  
### <a name="child-elements"></a>子元素

None
  
### <a name="parent-elements"></a>父元素  
  
| 項目         | 描述                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |  
| `runtime`       | 包含有關執行階段初始化選項的資訊。                                                        |  
  
## <a name="remarks"></a>備註  

從 .NET Framework 4.6 開始，通用語言執行時間預設會使用新的64位編譯器來進行即時（JIT）編譯。 在某些情況下，這可能會與舊版64位 JIT 編譯程式所 JIT 編譯的應用程式程式碼為有所差異。 藉由將 `<useLegacyJit>` 元素的 `enabled` 屬性設定為 [`1`]，您可以停用新的64位 JIT 編譯程式，並改為使用舊版64位 JIT 編譯程式來編譯您的應用程式。  
  
> [!NOTE]
> `<useLegacyJit>` 元素只會影響64位 JIT 編譯。 使用32位 JIT 編譯程式的編譯不受影響。  
  
除了使用設定檔設定之外，您還可以透過兩種方式啟用舊版的64位 JIT 編譯程式：  
  
- 設定環境變數

  將 `COMPLUS_useLegacyJit` 環境變數設定為 `0` （使用新的64位 JIT 編譯程式）或 `1` （使用較舊的64位 JIT 編譯程式）：
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  環境變數具有*全域範圍*，這表示它會影響電腦上執行的所有應用程式。 如果設定，應用程式佈建檔設定可以覆寫它。 環境變數名稱不區分大小寫。
  
- 新增登錄機碼

  您可以藉由將 `REG_DWORD` 值新增至登錄中的 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` 或 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` 機碼，來啟用舊版64位 JIT 編譯程式。 此值的名稱為 `useLegacyJit`。 如果值為0，則會使用新的編譯器。 如果值為1，則會啟用舊版64位 JIT 編譯程式。 登錄值名稱不區分大小寫。
  
  將值新增至 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` 金鑰會影響電腦上執行的所有應用程式。 將值新增至 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` 金鑰會影響目前使用者執行的所有應用程式。 如果電腦已設定多個使用者帳戶，則只有目前使用者執行的應用程式會受到影響，除非其他使用者的值也已加入登錄機碼中。 將 `<useLegacyJit>` 元素新增至設定檔會覆寫登錄設定（如果有的話）。  
  
## <a name="example"></a>範例  

下列設定檔會使用新的64位 JIT 編譯程式來停用編譯，而改用舊版的64位 JIT 編譯程式。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱

- [\<執行時間 > 元素](runtime-element.md)
- [\<configuration> 項目](../configuration-element.md)
- [風險降低：新的 64 位元 JIT 編譯器](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
