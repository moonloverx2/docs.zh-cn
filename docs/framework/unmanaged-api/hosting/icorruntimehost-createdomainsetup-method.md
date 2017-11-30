---
title: "ICorRuntimeHost::CreateDomainSetup 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomainSetup
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca09788ea403e2a60d6de0cb6834fdc90261b770
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="81b61-102">ICorRuntimeHost::CreateDomainSetup 方法</span><span class="sxs-lookup"><span data-stu-id="81b61-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="81b61-103">获取的接口指针的类型到 IAppDomainSetup<xref:System.AppDomainSetup?displayProperty=nameWithType>实例。</span><span class="sxs-lookup"><span data-stu-id="81b61-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="81b61-104">`IAppDomainSetup`提供用于配置应用程序域的方面，它将在创建之前方法。</span><span class="sxs-lookup"><span data-stu-id="81b61-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81b61-105">语法</span><span class="sxs-lookup"><span data-stu-id="81b61-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81b61-106">参数</span><span class="sxs-lookup"><span data-stu-id="81b61-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="81b61-107">[out]接口指针<xref:System.AppDomainSetup?displayProperty=nameWithType>实例。</span><span class="sxs-lookup"><span data-stu-id="81b61-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="81b61-108">此参数被类型化为`IUnknown`，因此通常应调用的调用方`QueryInterface`this 指针获取类型的接口指针上`IAppDomainSetup`。</span><span class="sxs-lookup"><span data-stu-id="81b61-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81b61-109">返回值</span><span class="sxs-lookup"><span data-stu-id="81b61-109">Return Value</span></span>  
  
|<span data-ttu-id="81b61-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81b61-110">HRESULT</span></span>|<span data-ttu-id="81b61-111">描述</span><span class="sxs-lookup"><span data-stu-id="81b61-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81b61-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="81b61-112">S_OK</span></span>|<span data-ttu-id="81b61-113">该操作成功。</span><span class="sxs-lookup"><span data-stu-id="81b61-113">The operation was successful.</span></span>|  
|<span data-ttu-id="81b61-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="81b61-114">S_FALSE</span></span>|<span data-ttu-id="81b61-115">操作无法完成。</span><span class="sxs-lookup"><span data-stu-id="81b61-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="81b61-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81b61-116">E_FAIL</span></span>|<span data-ttu-id="81b61-117">发生了未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="81b61-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="81b61-118">如果某方法返回 E_FAIL，公共语言运行时 (CLR) 不再可用进程中。</span><span class="sxs-lookup"><span data-stu-id="81b61-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="81b61-119">对任何托管 Api 的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="81b61-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="81b61-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81b61-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81b61-121">CLR 尚未加载到进程中，或 CLR 处于不能运行托管的代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="81b61-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81b61-122">备注</span><span class="sxs-lookup"><span data-stu-id="81b61-122">Remarks</span></span>  
 <span data-ttu-id="81b61-123">从此方法返回的指针通常传递作为参数传递给[CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="81b61-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81b61-124">要求</span><span class="sxs-lookup"><span data-stu-id="81b61-124">Requirements</span></span>  
 <span data-ttu-id="81b61-125">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81b61-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81b61-126">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="81b61-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81b61-127">**库：**作为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="81b61-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81b61-128">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="81b61-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81b61-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="81b61-129">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [<span data-ttu-id="81b61-130">ICorRuntimeHost 接口</span><span class="sxs-lookup"><span data-stu-id="81b61-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)