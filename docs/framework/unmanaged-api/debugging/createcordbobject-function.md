---
title: CreateCordbObject 函数
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12898f75d2575e539b018ea367bc870a3dc738a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406326"
---
# <a name="createcordbobject-function"></a>CreateCordbObject 函数
创建调试器界面 ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md))，提供用于实例化远程进程上托管的调试会话的功能。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
#### <a name="parameters"></a>参数  
 `iDebuggerVersion`  
 [in] 目标进程的调试器版本。 此参数必须为 CorDebugVersion_2_0 以用于远程调试。  
  
 `ppCordb`  
 [out]指针到指向的对象将被强制转换为[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)接口，并返回。  
  
## <a name="return-value"></a>返回值  
 S_OK  
 已成功确定该进程中的 CLR 的数目，并已正确填写相应的句柄数组和路径数组。  
  
 E_INVALIDARG  
 `ppCordb` 为 null，或 `iDebuggerVersion` 不是 CorDebugVersion_2_0。  
  
 E_OUTOFMEMORY  
 无法为 `ppCordb` 分配足够的内存  
  
 E_FAIL（或其他 E_ 返回代码）  
 其他故障。  
  
## <a name="remarks"></a>备注  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)中返回的接口`ppCordb`是所有托管调试服务的顶级调试接口。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CoreClrRemoteDebuggingInterfaces.h  
  
 **库：** mscordbi_macx86.dll  
  
 **.NET framework 版本：** 3.5 SP1
