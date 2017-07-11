1. from this folder run the command:

.. code:: bash

  git clone https://github.com/erik-geant/ansible-roles.git roles

2. edit ``Vagrantfile``, change the names in the bridge list to the actual names on your system


3. edit ``indico-dev.yml``

  - make sure only the ``indico`` role is uncommented

4. run:

.. code:: bash

  vagrant up


5. ssh into the machine and get the ip address assigned to the bridged interface

.. code:: bash

  vagrant ssh

.. code:: bash

  ip address
  exit


6. edit ``indico-dev.yml``

  - uncomment all but the ``indico-config`` role
  - change HOSTNAME to the address from above (probably the ipv4 address for enp0s8)


7. run:

  vagrant provision


8. log into the vm and set the basic indico configuration options, i.e. run the following:

.. code:: bash

  vagrant ssh

.. code:: bash

  sudo su - indico

  . .venv/bin/activate
  indico setup wizard

  # answer the questions, most defaults are ok except for:
  # - "Indico URL" should use the ip address from above as the hostname
  # - enter yourself for contact & admin email
  # - "SMTP host" should be "relay.geant.org"
  # - "Default timezone" press a key and use the drop-down boxes

  exit
  exit

9. edit ``indico-dev.yml``

  - uncomment all but the ``indico-launch`` role

10. run:

.. code:: bash

  vagrant provision


