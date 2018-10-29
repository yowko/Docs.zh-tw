---
title: 封送處理不同類型的陣列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0c71284fbc925aa9bb10a8bf68cef581f78d7f4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50088750"
---
# <a name="marshaling-different-types-of-arrays"></a>封送處理不同類型的陣列
陣列是 Managed 程式碼中的參考類型，它包含一或多個相同類型的項目。 雖然陣列是參考類型，它們會做為 In 參數傳遞至 Unmanaged 函式。 此行為與 Managed 陣列傳遞至 Managed 物件的方式 (做為 In/Out 參數) 不一致。 如需詳細資訊，請參閱 [複製和固定](copying-and-pinning.md)。  
  
 下表列出陣列的封送處理選項，並說明其用法。  
  
|陣列|描述|  
|-----------|-----------------|  
|傳值方式的整數。|將整數的陣列做為 In 參數傳遞。|  
|傳址方式的整數。|將整數的陣列做為 In/Out 參數傳遞。|  
|傳值方式的整數 (二維)。|將整數的矩陣做為 In 參數傳遞。|  
|傳值方式的字串。|將字串的陣列做為 In 參數傳遞。|  
|整數的結構。|將包含整數的結構陣列做為 In/Out 參數傳遞。|  
|字串的結構。|將僅包含整數的結構陣列做為 In/Out 參數傳遞。 可變更陣列的成員。|  
  
## <a name="example"></a>範例  
 本範例示範如何傳遞下列類型的陣列：  
  
-   傳值方式的整數陣列。  
  
-   傳址方式的整數陣列，可調整大小。  
  
-   傳值方式的整數多維度陣列 (矩陣)。  
  
-   傳值方式的字串陣列。  
  
-   整數的結構陣列。  
  
-   字串的結構陣列。  
  
 除非陣列是明確地以傳值方式封送處理，否則預設行為會將陣列封送處理做為 In 參數。 您可以明確套用 <xref:System.Runtime.InteropServices.InAttribute> 和 <xref:System.Runtime.InteropServices.OutAttribute> 屬性來變更此行為。  
  
 陣列範例會使用下列 Unmanaged 函式，和其原始函式宣告：  
  
-   從 PinvokeLib.dll 匯出的**TestArrayOfInts** 。  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   從 PinvokeLib.dll 匯出的**TestRefArrayOfInts** 。  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   從 PinvokeLib.dll 匯出的**TestMatrixOfInts** 。  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   從 PinvokeLib.dll 匯出的**TestArrayOfStrings** 。  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   從 PinvokeLib.dll 匯出的**TestArrayOfStructs** 。  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   從 PinvokeLib.dll 匯出的**TestArrayOfStructs2** 。  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [PinvokeLib.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as6wyhwt(v=vs.100)) 是自訂的 Unmanaged 程式庫，包含先前所列出函式和 2 個結構變數的實作： **MYPOINT** 和 **MYPERSON**。 這些結構包含下列項目：  
  
```  
typedef struct _MYPOINT  
{  
   int x;   
   int y;   
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;   
   char* last;   
} MYPERSON;  
```  
  
 在此範例中，`MyPoint` 和 `MyPerson` 結構包含內嵌類型。 已設定 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性來確定此成員以其顯示的順序循序排列在記憶體中。  
  
 `LibWrap` 類別包含一組 `App` 類別所呼叫的方法。 如需傳遞陣列的特定詳細資訊，請參閱下面範例中的註解。 陣列是參考類型，它預設是做為 In 參數傳遞。 呼叫端若要接收結果， **InAttribute** 和 **OutAttribute** 必須明確地套用至包含陣列的引數。  
  
### <a name="declaring-prototypes"></a>宣告原型  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>呼叫函式  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>請參閱  
 [封送處理類型的陣列](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))  
 [平台叫用資料類型](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [在 Managed 程式碼中建立原型](creating-prototypes-in-managed-code.md)
