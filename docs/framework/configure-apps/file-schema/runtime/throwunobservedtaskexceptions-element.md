---
title: "&lt;ThrowUnobservedTaskExceptions&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d171c2058a79476d99c5952cc6a697f126af81c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltthrowunobservedtaskexceptionsgt-element"></a>&lt;ThrowUnobservedTaskExceptions&gt;項目
指定未處理的工作例外狀況是否應終止執行中的處理序。  
  
 \<configuration>  
\<執行階段 >  
\<ThrowUnobservedTaskExceptions >  
  
## <a name="syntax"></a>語法  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定的例外狀況處理的工作是否終止執行中處理序。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|說明|  
|-----------|-----------------|  
|`false`|不會終止例外狀況處理的工作執行的處理序。 這是預設值。|  
|`true`|終止執行中處理序例外狀況處理的工作。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
|||  
  
## <a name="remarks"></a>備註  
 如果相關聯的例外狀況<xref:System.Threading.Tasks.Task>發現，沒有任何<xref:System.Threading.Tasks.Task.Wait%2A>未連接父代的作業，而<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType>屬性未讀取的工作例外狀況會被視為未觀察到。  
  
 在[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]，依預設，如果<xref:System.Threading.Tasks.Task>具有未觀察到的例外是記憶體回收中，完成項擲回例外狀況和終止處理序。 終止處理序取決於記憶體回收和最終處理的時機。  
  
 若要簡化開發人員撰寫非同步程式碼，根據工作，[!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]變成未觀察到的例外狀況的這個預設行為。 未觀察到的例外狀況，仍然會使<xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException>會引發事件，但根據預設，處理程序不會終止。 相反地之後會引發事件，不論是否事件處理常式會觀察到的例外狀況,，則會忽略例外狀況。  
  
 在[!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]，您可以使用[ \<ThrowUnobservedTaskExceptions > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)應用程式組態檔中啟用[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]擲回例外狀況的行為。  
  
 您也可以下列方式之一，指定例外狀況行為：  
  
-   設定環境變數`COMPlus_ThrowUnobservedTaskExceptions`(`set COMPlus_ThrowUnobservedTaskExceptions=1`)。  
  
-   藉由設定登錄 DWORD 值 ThrowUnobservedTaskExceptions = 1 中 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\。NETFramework 索引鍵。  
  
## <a name="example"></a>範例  
 下列範例會示範如何啟用擲回的例外狀況，在工作中使用應用程式組態檔。  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>範例  
 下列範例會示範如何從工作擲回未觀察到的例外狀況。 程式碼必須執行以發行的程式正常運作。  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
