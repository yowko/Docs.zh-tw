---
title: 使用序列化繫結器
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: bfce2a14c8757250c520919c8ff2a4d7048a9d5c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138657"
---
# <a name="usage-of-serialization-binder"></a>使用序列化繫結器
此範例示範如何使用 <xref:System.Runtime.Serialization.SerializationBinder> 變更序列化時一般類型的版本。  
  
## <a name="demonstrates"></a>示範  
 <xref:System.Runtime.Serialization.SerializationBinder>、 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>討論  
 這個範例示範兩個以不同 .NET Framework 版本為目標的實體如何使用二進位格式器和序列化系結器來進行通訊。  
  
這個範例是使用 .NET 遠端處理所開發的。 其包含以 .NET Framework 4 為目標的伺服器，其可執行具有泛型型別的合約，以及兩個不同的用戶端，一個目標為 .NET Framework 2.0，另一個目標為 .NET Framework 4。  
  
 伺服器會將 <xref:System.Runtime.Serialization.SerializationBinder> 附加到 Binary Formatter 以便能夠根據序列化變更型別的版本，因此，兩個用戶端都可以正確還原序列化這些型別。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要設定、建置及執行範例  
  
1. 若要執行用戶端，請以滑鼠右鍵按一下方案 [SBGenericsVTS （6個專案）]，然後選取 [**屬性**]。  
  
2. 在 [**通用屬性**] 中，選取 [**啟始專案**]，然後選取 [**多個啟始專案**]。  
  
3. 依序選取 [ **Server** first]、[ **Client20** ] 和 [ **Client40**]。 選取這三個專案的 [**啟動**] 動作，並將其餘設定保留為 [**無**]。  
  
4. 按一下 **[確定]** ，然後按 F5 執行範例。
