# angularpyramid

A learning experience using Angularjs and Python Pyramid
Using the pyramid_angularstarter scaffolding library (https://pypi.python.org/pypi/pyramid_angularstarter)

### Build steps
- $ git clone https://github.com/CodyReichert/angularpyramid.git
- $ cd angularpyramid
- $ virtualenv --no-site-packages env
- $ source env/bin/activate
 ($ deactive at any time)
- $ easy_install sqlalchemy
- $ python setup.py develop

#### Run
- $ pserve development.ini --reload
- To have gulp watch your coffeescript and sass:

  $ cd angularpyramid/client-src && gulp watch

#### Other dependencies
- $ cd angularpyramid/client-src
- $ npm install && bower install && gulp


#### Database Setup
- $ alembic revision --autogenerate -m "initial"
- $ vim migration/version/GENERATED FILE FROM LAST STEP
- add line:

    from sqlalchemy_utils.types.password import PasswordType

  replace line:

    sa.Column('password', sa.PasswordType(length=1137), nullable=True)

  with line:

    sa.Column('password', PasswordType(), nullable=True)

- $ alembic upgrade head


####Email Setup (top level)
- $ touch secret_settings.ini
- insert lines:

    [secrets]

    mail.transport.username = youremailaddress@gmail.com

    mail.transport.password = yourgmailpassword
