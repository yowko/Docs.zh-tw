---
title: CorDebugRegister 列舉
ms.date: 03/30/2017
api_name:
- CorDebugRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugRegister
helpviewer_keywords:
- CorDebugRegister enumeration [.NET Framework debugging]
ms.assetid: 003bb138-7960-4291-ac88-0d87e470ff70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4175cf26b783ab7f19905941e94cfdb15ce69cff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694057"
---
# <a name="cordebugregister-enumeration"></a>CorDebugRegister 列舉
指定與給定處理器架構相關聯的暫存器。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorDebugRegister {  
  
    REGISTER_INSTRUCTION_POINTER = 0,  
    REGISTER_STACK_POINTER,  
    REGISTER_FRAME_POINTER,  
  
    REGISTER_X86_EIP = 0,  
    REGISTER_X86_ESP,  
    REGISTER_X86_EBP,  
  
    REGISTER_X86_EAX,  
    REGISTER_X86_ECX,  
    REGISTER_X86_EDX,  
    REGISTER_X86_EBX,  
  
    REGISTER_X86_ESI,  
    REGISTER_X86_EDI,  
  
    REGISTER_X86_FPSTACK_0,  
    REGISTER_X86_FPSTACK_1,  
    REGISTER_X86_FPSTACK_2,  
    REGISTER_X86_FPSTACK_3,  
    REGISTER_X86_FPSTACK_4,  
    REGISTER_X86_FPSTACK_5,  
    REGISTER_X86_FPSTACK_6,  
    REGISTER_X86_FPSTACK_7,  
  
    REGISTER_AMD64_RIP = 0,  
    REGISTER_AMD64_RSP,  
    REGISTER_AMD64_RBP,  
    REGISTER_AMD64_RAX,  
    REGISTER_AMD64_RCX,  
    REGISTER_AMD64_RDX,  
    REGISTER_AMD64_RBX,  
    REGISTER_AMD64_RSI,  
    REGISTER_AMD64_RDI,  
    REGISTER_AMD64_R8,  
    REGISTER_AMD64_R9,  
    REGISTER_AMD64_R10,  
    REGISTER_AMD64_R11,  
    REGISTER_AMD64_R12,  
    REGISTER_AMD64_R13,  
    REGISTER_AMD64_R14,  
    REGISTER_AMD64_R15,  
  
    REGISTER_AMD64_XMM0,  
    REGISTER_AMD64_XMM1,  
    REGISTER_AMD64_XMM2,  
    REGISTER_AMD64_XMM3,  
    REGISTER_AMD64_XMM4,  
    REGISTER_AMD64_XMM5,  
    REGISTER_AMD64_XMM6,  
    REGISTER_AMD64_XMM7,  
    REGISTER_AMD64_XMM8,  
    REGISTER_AMD64_XMM9,  
    REGISTER_AMD64_XMM10,  
    REGISTER_AMD64_XMM11,  
    REGISTER_AMD64_XMM12,  
    REGISTER_AMD64_XMM13,  
    REGISTER_AMD64_XMM14,  
    REGISTER_AMD64_XMM15,  
  
    REGISTER_IA64_BSP = REGISTER_FRAME_POINTER,  
    REGISTER_IA64_R0  = REGISTER_IA64_BSP + 1,  
    REGISTER_IA64_F0  = REGISTER_IA64_R0  + 128,  
    REGISTER_ARM_PC = 0,  
    REGISTER_ARM_SP,  
    REGISTER_ARM_R0,  
    REGISTER_ARM_R1,  
    REGISTER_ARM_R2,  
    REGISTER_ARM_R3,  
    REGISTER_ARM_R4,  
    REGISTER_ARM_R5,  
    REGISTER_ARM_R6,  
    REGISTER_ARM_R7,  
    REGISTER_ARM_R8,  
    REGISTER_ARM_R9,  
    REGISTER_ARM_R10,  
    REGISTER_ARM_R11,  
    REGISTER_ARM_R12,  
    REGISTER_ARM_LR,  
  
} CorDebugRegister;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|處理器上的指令指標暫存器。|  
|`REGISTER_STACK_POINTER`|處理器上的堆疊指標暫存器。|  
|`REGISTER_FRAME_POINTER`|處理器上的框架指標暫存器。|  
|`REGISTER_X86_EIP`|x86 處理器上的指令指標暫存器。|  
|`REGISTER_X86_ESP`|x86 處理器上的堆疊指標暫存器。|  
|`REGISTER_X86_EBP`|x86 處理器上的基底指標暫存器。|  
|`REGISTER_X86_EAX`|x86 處理器上的 A 資料暫存器。|  
|`REGISTER_X86_ECX`|x86 處理器上的 C 資料暫存器。|  
|`REGISTER_X86_EDX`|x86 處理器上的 D 資料暫存器。|  
|`REGISTER_X86_EBX`|x86 處理器上的 B 資料暫存器。|  
|`REGISTER_X86_ESI`|x86 處理器上的來源索引暫存器。|  
|`REGISTER_X86_EDI`|x86 處理器上的目的地索引暫存器。|  
|`REGISTER_X86_FPSTACK_0`|x86 浮點 (FP) 處理器上的堆疊暫存器 0。|  
|`REGISTER_X86_FPSTACK_1`|x86 FP 處理器上的 #1 堆疊暫存器。|  
|`REGISTER_X86_FPSTACK_2`|x86 FP 處理器上的 #2 堆疊暫存器。|  
|`REGISTER_X86_FPSTACK_3`|x86 FP 處理器上的 #3 堆疊暫存器。|  
|`REGISTER_X86_FPSTACK_4`|x86 FP 處理器上的 #4 堆疊暫存器。|  
|`REGISTER_X86_FPSTACK_5`|x86 FP 處理器上的 #5 堆疊暫存器。|  
|`REGISTER_X86_FPSTACK_6`|x86 FP 處理器上的 #6 堆疊暫存器。|  
|`REGISTER_X86_FPSTACK_7`|x86 FP 處理器上的 #7 堆疊暫存器。|  
|`REGISTER_AMD64_RIP`|AMD64 處理器上的指令指標暫存器。|  
|`REGISTER_AMD64_RSP`|AMD64 處理器上的堆疊指標暫存器。|  
|`REGISTER_AMD64_RBP`|AMD64 處理器上的基底指標暫存器。|  
|`REGISTER_AMD64_RAX`|AMD64 處理器上的 A 資料暫存器。|  
|`REGISTER_AMD64_RCX`|AMD64 處理器上的 C 資料暫存器。|  
|`REGISTER_AMD64_RDX`|AMD64 處理器上的 D 資料暫存器。|  
|`REGISTER_AMD64_RBX`|AMD64 處理器上的 B 資料暫存器。|  
|`REGISTER_AMD64_RSI`|AMD64 處理器上的來源索引暫存器。|  
|`REGISTER_AMD64_RDI`|AMD64 處理器上的目的地索引暫存器。|  
|`REGISTER_AMD64_R8`|AMD64 處理器上的 #8 資料暫存器。|  
|`REGISTER_AMD64_R9`|AMD64 處理器上的 #9 資料暫存器。|  
|`REGISTER_AMD64_R10`|AMD64 處理器上的 #10 資料暫存器。|  
|`REGISTER_AMD64_R11`|AMD64 處理器上的 #11 資料暫存器。|  
|`REGISTER_AMD64_R12`|AMD64 處理器上的 #12 資料暫存器。|  
|`REGISTER_AMD64_R13`|AMD64 處理器上的 #13 資料暫存器。|  
|`REGISTER_AMD64_R14`|AMD64 處理器上的 #14 資料暫存器。|  
|`REGISTER_AMD64_R15`|AMD64 處理器上的 #15 資料暫存器。|  
|`REGISTER_AMD64_XMM0`|AMD64 處理器上的 #0 多媒體暫存器。|  
|`REGISTER_AMD64_XMM1`|AMD64 處理器上的 #1 多媒體暫存器。|  
|`REGISTER_AMD64_XMM2`|AMD64 處理器上的 #2 多媒體暫存器。|  
|`REGISTER_AMD64_XMM3`|AMD64 處理器上的 #3 多媒體暫存器。|  
|`REGISTER_AMD64_XMM4`|AMD64 處理器上的 #4 多媒體暫存器。|  
|`REGISTER_AMD64_XMM5`|AMD64 處理器上的 #5 多媒體暫存器。|  
|`REGISTER_AMD64_XMM6`|AMD64 處理器上的 #6 多媒體暫存器。|  
|`REGISTER_AMD64_XMM7`|AMD64 處理器上的 #7 多媒體暫存器。|  
|`REGISTER_AMD64_XMM8`|AMD64 處理器上的 #8 多媒體暫存器。|  
|`REGISTER_AMD64_XMM9`|AMD64 處理器上的 #9 多媒體暫存器。|  
|`REGISTER_AMD64_XMM10`|AMD64 處理器上的 #10 多媒體暫存器。|  
|`REGISTER_AMD64_XMM11`|AMD64 處理器上的 #11 多媒體暫存器。|  
|`REGISTER_AMD64_XMM12`|AMD64 處理器上的 #12 多媒體暫存器。|  
|`REGISTER_AMD64_XMM13`|AMD64 處理器上的 #13 多媒體暫存器。|  
|`REGISTER_AMD64_XMM14`|AMD64 處理器上的 #14 多媒體暫存器。|  
|`REGISTER_AMD64_XMM15`|AMD64 處理器上的 #15 多媒體暫存器。|  
|`REGISTER_IA64_BSP`|IA-64 處理器上的堆疊指標暫存器。|  
|`REGISTER_IA64_R0`|IA-64 處理器上的 #0 資料暫存器。|  
|`REGISTER_IA64_F0`|IA-64 處理器上的 #0 FP 資料暫存器。|  
|`REGISTER_ARM_PC`|ARM 處理器上的程式計數器暫存器 (R15)。|  
|`REGISTER_ARM_SP`|ARM 處理器上的堆疊指標暫存器 (R13)。|  
|`REGISTER_ARM_R0`|ARM 處理器上的資料暫存器 R0。|  
|`REGISTER_ARM_R1`|ARM 處理器上的資料暫存器 R1。|  
|`REGISTER_ARM_R2`|ARM 處理器上的資料暫存器 R2。|  
|`REGISTER_ARM_R3`|ARM 處理器上的資料暫存器 R3。|  
|`REGISTER_ARM_R4`|ARM 處理器上的暫存器 R4。|  
|`REGISTER_ARM_R5`|ARM 處理器上的暫存器 R5。|  
|`REGISTER_ARM_R6`|ARM 處理器上的暫存器 R6。|  
|`REGISTER_ARM_R7`|ARM 處理器上的暫存器 R7 (THUMB 框架指標)。|  
|`REGISTER_ARM_R8`|ARM 處理器上的暫存器 R8。|  
|`REGISTER_ARM_R9`|ARM 處理器上的暫存器 R9。|  
|`REGISTER_ARM_R10`|ARM 處理器上的暫存器 R10。|  
|`REGISTER_ARM_R11`|ARM 處理器上的框架指標。|  
|`REGISTER_ARM_R12`|ARM 處理器上的暫存器 R12。|  
|`REGISTER_ARM_LR`|ARM 處理器上的連結暫存器 (R14)。|  
  
## <a name="remarks"></a>備註  
 IA-64 處理器上共有 128 個一般用途的資料暫存器，以及 128 個浮點資料暫存器，但只會提供值 `REGISTER_IA64_R0` 與 `REGISTER_IA64_F0`。 其他值可以透過下列方法指定：  
  
-   將值 `REGISTER_IA64_R0` 到 `REGISTER_IA64_R1` (對應到 IA-64 處理器上的資料暫存器 #1 到 #127) 的暫存器號碼加入 `REGISTER_IA64_R127`。  
  
-   將值 `REGISTER_IA64_F0` 到 `REGISTER_IA64_F1` (對應到 IA-64 處理器上的資料暫存器 #1 FP 到 #127 FP) 的暫存器號碼加入 `REGISTER_IA64_F127`。  
  
 例如，若您需要指定 IA-64 處理器上的 #83 資料暫存器，可使用 `REGISTER_IA64_R0` + 83。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
