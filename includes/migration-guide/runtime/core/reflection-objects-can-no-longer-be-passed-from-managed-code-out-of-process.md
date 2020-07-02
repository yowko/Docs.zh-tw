---
ms.openlocfilehash: a54b17b2002bd0f85b8b47c5e37e040470d6c494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621144"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>無法再將反映物件從受控程式碼傳遞至跨處理序的 DCOM 用戶端

#### <a name="details"></a>詳細資料

無法再將反映物件從 Managed 程式碼傳遞至跨處理序的 DCOM 用戶端。 以下是受到影響的類型：<ul><li><xref:System.Reflection.Assembly?displayProperty=fullName></li><li><xref:System.Reflection.MemberInfo?displayProperty=fullName> (和其衍生的類型，包括 <xref:System.Reflection.FieldInfo?displayProperty=fullName>、<xref:System.Reflection.MethodInfo?displayProperty=fullName>、<xref:System.Type?displayProperty=fullName> 和 <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</li><li><xref:System.Reflection.MethodBody?displayProperty=fullName></li><li><xref:System.Reflection.Module?displayProperty=fullName></li><li><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</li></ul>呼叫物件的 <code>IMarshal</code> 會傳回 <code>E_NOINTERFACE</code>。

#### <a name="suggestion"></a>建議

請更新封送處理程式碼以搭配非反映物件使用

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.6|
|類型|執行階段|
