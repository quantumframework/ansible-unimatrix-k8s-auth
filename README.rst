``unimatrix-k8s-auth``
======================
Configure local Kubernetes authentication for use with
Ansible playbooks.

Requirements
------------
None specified.

Role Variables
--------------
None specified.

Dependencies
------------
The following Python modules should be installed:

- ``openshift``

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

.. code:: yaml

  - hosts: localhost
    roles:
    - unimatrix-k8s-auth
    tasks:
    - name: lookup all namespaces
      register: result
      k8s_facts:
        kubeconfig: "{{ k8s_kubeconfig }}"
        kind: Namespace

    - name: display information about namespaces
      with_items: "{{ result.resources }}"
      loop_control:
        loop_var: ns
      debug:
        msg: "{{ ns.metadata.name }}"

License
-------
BSD

Author Information
------------------
cochise.ruhulessin@wizardsofindustry.com
