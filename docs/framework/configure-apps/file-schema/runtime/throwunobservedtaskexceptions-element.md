---
title: <ThrowUnobservedTaskExceptions> 項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9647297bf976d26a97be0da8807d607789e8a065
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489582"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedTaskExceptions > 項目
指定未處理的工作例外狀況是否應終止執行中的處理序。  
  
 \<configuration>  
\<執行階段 >  
\<ThrowUnobservedTaskExceptions>  
  
## <a name="syntax"></a>語法  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定未處理的工作例外狀況是否終止執行中處理序。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不會終止執行中處理序例外狀況未處理的工作。 這是預設值。|  
|`true`|終止執行中處理序例外狀況未處理的工作。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
|||  
  
## <a name="remarks"></a>備註  
 如果例外狀況相關聯<xref:System.Threading.Tasks.Task>尚未發現，沒有任何<xref:System.Threading.Tasks.Task.Wait%2A>未附加作業，父代，而<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType>屬性未讀取的工作例外狀況會被視為未觀察到。  
  
 在.NET Framework 4 中，根據預設，如果<xref:System.Threading.Tasks.Task>具有未觀察到例外狀況是記憶體回收，完成項會擲回例外狀況，並終止處理序。 終止處理序取決於記憶體回收行程和終結的時機。  
  
 若要簡化開發人員撰寫工作為基礎的非同步程式碼，.NET Framework 4.5 中變更此預設行為未觀察到的例外狀況。 未觀察到的例外狀況，仍有導致<xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException>事件引發，但根據預設，此程序不會終止。 相反地，引發事件，不論事件處理常式是否會觀察到例外狀況之後，會忽略例外狀況。  
  
 在.NET Framework 4.5 中，您可以使用[ \<ThrowUnobservedTaskExceptions > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)應用程式組態檔中啟用.NET Framework 4 的行為擲回例外狀況。  
  
 您也可以指定的例外狀況行為中的下列方法之一：  
  
- 藉由設定環境變數`COMPlus_ThrowUnobservedTaskExceptions`(`set COMPlus_ThrowUnobservedTaskExceptions=1`)。  
  
- 藉由設定登錄 DWORD 值 ThrowUnobservedTaskExceptions = 1 在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\。NETFramework 索引鍵。  
  
## <a name="example"></a>範例  
 下列範例示範如何啟用擲回的例外狀況，在工作中使用應用程式組態檔。  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>範例  
 下列範例會示範如何從工作擲回未觀察到的例外狀況。 為發行的程式正常運作，必須執行的程式碼。  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
