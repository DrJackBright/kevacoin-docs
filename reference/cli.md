# Kevacoin Client/API calls list

## Key-value related operations

## **keva_namespace**  `<display_name>`

Create a namepsace with the given display name.

**Arguments**

1. `<display_name>`: &nbsp; (string, &nbsp; required) &nbsp;  The display name of the namespace. This is for your internal use only and does not require to be unique across the network.

**Results**
<pre>
[
    {
        txid: xxxxxxxxxxxxxx,  (string) Transaction Id
        namespaceId: Nxxxxxx   (string) Unique namespace id, with "N" prefix.
    }
]
</pre>

**Examples**
<pre>
kevacoin-cli keva_namespace "my first namespace"
</pre>

## **keva_list_namespaces**

List all the namespaces belong to the current wallet.

**Arguments**

**Results**
<pre>
[
    {
        txid: xxxxxxxxxxxxxx,  (string) Transaction Id
        namespaceId: Nxxxxxx   (string) Unique namespace id, with "N" prefix.
    }
]
</pre>

**Examples**
<pre>
kevacoin-cli keva_list_namespaces
</pre>




