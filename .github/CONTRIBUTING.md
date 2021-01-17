# How to contribute

Thanks! There are a few guidelines that we need contributors to follow so that we can keep on top of things.

## Report

You can report bugs or make enhancement requests at this [GitHub project issue page](http://github.com/rembik/ansible-role-kickstart-iso/issues/new/choose) by filling out the issue template that will be presented.

## Develop

You are very welcome to develop bug fixes or features. Please make sure to run tests before making a [pull request](https://help.github.com/articles/creating-a-pull-request/) to this GitHub project.

## Test

This role uses [Molecule](https://github.com/ansible-community/molecule) for testing and that, in turn, uses Ansible to deploy the needed test infrastructure:
```
sudo pip install ansible
sudo pip install molecule
```

Furthermore, tests use Docker. Follow the respective requirements for that:
- [Docker](http://github.com/rembik/ansible-role-kickstart-iso/tree/master/molecule/default/INSTALL.rst)

Then run the test with the chosen molecule scenario:
```
molecule test
molecule test --scenario-name docker-all-latest
```

In addition, if you want to run the tests on different Ansible versions locally with Docker use [tox](https://tox.readthedocs.io/en/latest/):
```
sudo pip install tox

tox
```
