---
UID: NF:winfax.FaxEnumPortsW
title: FaxEnumPortsW function (winfax.h)
description: The FaxEnumPorts function enumerates all fax devices currently attached to the fax server to which the client has connected. The function returns detailed information for each fax port to the fax client application.
helpviewer_keywords: ["FaxEnumPorts","FaxEnumPorts function [Fax Service]","FaxEnumPortsA","FaxEnumPortsW","_mfax_faxenumports","fax._mfax_faxenumports","winfax/FaxEnumPorts","winfax/FaxEnumPortsA","winfax/FaxEnumPortsW"]
old-location: fax\_mfax_faxenumports.htm
tech.root: Fax
ms.assetid: VS|fax|~\fax\faxlegacy_0ir7.htm
ms.date: 12/05/2018
ms.keywords: FaxEnumPorts, FaxEnumPorts function [Fax Service], FaxEnumPortsA, FaxEnumPortsW, _mfax_faxenumports, fax._mfax_faxenumports, winfax/FaxEnumPorts, winfax/FaxEnumPortsA, winfax/FaxEnumPortsW
req.header: winfax.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 2000 Professional [desktop apps only]
req.target-min-winversvr: Windows 2000 Server [desktop apps only]
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: FaxEnumPortsW (Unicode) and FaxEnumPortsA (ANSI)
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: WinFax.lib
req.dll: 
req.irql: 
targetos: Windows
req.typenames: 
req.redist: 
ms.custom: 19H1
f1_keywords:
 - FaxEnumPortsW
 - winfax/FaxEnumPortsW
dev_langs:
 - c++
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - LibDef
api_location:
 - WinFax.lib
 - WinFax.dll
api_name:
 - FaxEnumPorts
 - FaxEnumPortsA
 - FaxEnumPortsW
---

# FaxEnumPortsW function


## -description

The <b>FaxEnumPorts</b> function enumerates all fax devices currently attached to the fax server to which the client has connected. The function returns detailed information for each fax port to the fax client application.

## -parameters

### -param FaxHandle [in]

Type: <b>HANDLE</b>

Specifies a fax server handle returned by a call to the <a href="/previous-versions/windows/desktop/api/winfax/nf-winfax-faxconnectfaxservera">FaxConnectFaxServer</a> function.

### -param PortInfo [out]

Type: <b>PFAX_PORT_INFO*</b>

Pointer to the address of a buffer to receive an array of <a href="/windows/desktop/api/winfax/ns-winfax-fax_port_infoa">FAX_PORT_INFO</a> structures. Each structure describes one fax port. The data includes, among other items, the permanent line identifier, and the current status and capability of the port. For information about memory allocation, see the following Remarks section.

### -param PortsReturned [out]

Type: <b>LPDWORD</b>

Pointer to a <b>DWORD</b> variable to receive the number of <a href="/windows/desktop/api/winfax/ns-winfax-fax_port_infoa">FAX_PORT_INFO</a> structures the function returns in the <i>PortInfo</i> parameter.

## -returns

Type: <b>BOOL</b>

If the function succeeds, the return value is nonzero.

If the function fails, the return value is zero. To get extended error information, call <a href="/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror">GetLastError</a>. GetLastError can return one of the following errors.

<table>
<tr>
<th>Return code</th>
<th>Description</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>ERROR_ACCESS_DENIED</b></dt>
</dl>
</td>
<td width="60%">
Access is denied. <a href="/previous-versions/windows/desktop/fax/-mfax-specific-fax-access-rights">FAX_JOB_QUERY</a> access is required.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>ERROR_INVALID_PARAMETER</b></dt>
</dl>
</td>
<td width="60%">
One or all of the <i>PortsReturned</i>, <i>PortInfo</i>, or <i>FaxHandle</i> parameters are <b>NULL</b>.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>ERROR_NOT_ENOUGH_MEMORY</b></dt>
</dl>
</td>
<td width="60%">
An error occurred during memory allocation.

</td>
</tr>
</table>

## -remarks

The <b>FaxEnumPorts</b> function returns a list of fax jobs on the fax server of interest, as well as information available about each job. A fax administration application typically calls this function to display the fax job queue for administrative or query purposes. For more information, see <a href="/previous-versions/windows/desktop/fax/-mfax-managing-fax-jobs">Managing Fax Jobs</a>.

The <b>FaxEnumPorts</b> function allocates the memory required for the <a href="/windows/desktop/api/winfax/ns-winfax-fax_job_entrya">FAX_JOB_ENTRY</a> buffer array pointed to by the <i>JobEntry</i> parameter. An application must call the <a href="/previous-versions/windows/desktop/api/winfax/nc-winfax-pfaxfreebuffer">FaxFreeBuffer</a> function to deallocate the resources associated with this parameter. For more information, see <a href="/previous-versions/windows/desktop/fax/-mfax-freeing-fax-resources">Freeing Fax Resources</a>.





> [!NOTE]
> The winfax.h header defines FaxEnumPorts as an alias which automatically selects the ANSI or Unicode version of this function based on the definition of the UNICODE preprocessor constant. Mixing usage of the encoding-neutral alias with code that not encoding-neutral can lead to mismatches that result in compilation or runtime errors. For more information, see [Conventions for Function Prototypes](/windows/win32/intl/conventions-for-function-prototypes).

## -see-also

<a href="/windows/desktop/api/winfax/ns-winfax-fax_job_entrya">FAX_JOB_ENTRY</a>



<a href="/previous-versions/windows/desktop/fax/-mfax-fax-service-client-api-functions">Fax Service Client API Functions</a>



<a href="/previous-versions/windows/desktop/fax/-mfax-fax-service-client-api-for-windows-2000">Fax Service Client API for Windows 2000</a>



<a href="/previous-versions/windows/desktop/api/winfax/nf-winfax-faxconnectfaxservera">FaxConnectFaxServer</a>



<a href="/previous-versions/windows/desktop/api/winfax/nc-winfax-pfaxfreebuffer">FaxFreeBuffer</a>



<a href="/previous-versions/windows/desktop/api/winfax/nf-winfax-faxgetjoba">FaxGetJob</a>