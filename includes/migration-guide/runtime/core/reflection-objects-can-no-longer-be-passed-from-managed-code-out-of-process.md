---
ms.openlocfilehash: 38c774417fc94fa080bf2b82c04d575e9068cdcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858580"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>無法再將反映物件從受控程式碼傳遞至跨處理序的 DCOM 用戶端

|   |   |
|---|---|
|詳細資料|無法再將反映物件從 Managed 程式碼傳遞至跨處理序的 DCOM 用戶端。 以下是受到影響的類型：<ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name> (和其衍生的類型，包括 <xref:System.Reflection.FieldInfo?displayProperty=name>、<xref:System.Reflection.MethodInfo?displayProperty=name>、<xref:System.Type?displayProperty=name> 和 <xref:System.Reflection.TypeInfo?displayProperty=name>)</li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name>.</li></ul>呼叫物件的 <code>IMarshal</code> 會傳回 <code>E_NOINTERFACE</code>。|
|建議|請更新封送處理程式碼以搭配非反映物件使用|
|影響範圍|Minor|
|版本|4.6|
|類型|執行階段|
