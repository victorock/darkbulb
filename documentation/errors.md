Collection of Errors hit during provisioning and how to solve them

# Error Git clone error
```
TASK [darkbulb : Git clone Darkbulb content to student's home] ***********************************************************************************************************************
fatal: [student01]: FAILED! => {
    "before": "2ab816a328ef36428b0d4bab43ae12814b424888",
    "changed": false
}

MSG:

Local modifications exist in repository (force=no).
```
Not sure yet... needed to change force: true but this makes me worry about idempotence

# Error PyCrypto Library
```
TASK [darkbulb : Create student instance] ********************************************************************************************************************************************
fatal: [localhost]: FAILED! => {
    "changed": false
}

MSG:

Unexpected response: ('PyCrypto library required for Service Account Authentication.'). Detail: Traceback (most recent call last):
  File "/var/folders/yg/mfwqk87930l5hsxkwt8r_0s40000gp/T/ansible_BRji_B/ansible_modlib.zip/ansible/module_utils/gcp.py", line 287, in gcp_connect
    project=creds['project_id'])
  File "/Library/Python/2.7/site-packages/libcloud/compute/drivers/gce.py", line 1795, in __init__
    super(GCENodeDriver, self).__init__(user_id, key, **kwargs)
  File "/Library/Python/2.7/site-packages/libcloud/common/base.py", line 975, in __init__
    self.connection = self.connectionCls(*args, **conn_kwargs)
  File "/Library/Python/2.7/site-packages/libcloud/compute/drivers/gce.py", line 99, in __init__
    credential_file=credential_file, **kwargs)
  File "/Library/Python/2.7/site-packages/libcloud/common/google.py", line 767, in __init__
    user_id, key, auth_type, credential_file, scopes, **kwargs)
  File "/Library/Python/2.7/site-packages/libcloud/common/google.py", line 653, in __init__
    self.user_id, self.key, self.scopes, **kwargs)
  File "/Library/Python/2.7/site-packages/libcloud/common/google.py", line 486, in __init__
    raise GoogleAuthError('PyCrypto library required for '
GoogleAuthError: 'PyCrypto library required for Service Account Authentication.'
```
Need to make sure PyCrypto is installed:
``pip install PyCrypto```

# Error libcloud

```
fatal: [localhost]: FAILED! => {
    "changed": false
}

MSG:

libcloud with GCE support (0.17.0+) required for this module
```
Need to make sure apache-libcloud is installed
```$ pip install apache-libcloud```
