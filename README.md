AWS Simple Mock Metadata
========================

The AWS ec2 instance metadata service runs on each ec2 instance and provide an api to get credentials based on the IAM role.

I needed to run this service locally in order to be able to troubleshoot issues with my docker containers running later on ECS. I tried the much more powerful [aws-mock-metadata](https://github.com/jtblin/aws-mock-metadata) but could not get it running. So I decided to build a very small python based service fitting my needs. The main goal is keep it very simple. So feel free to clone for you. You can also submit pull request.

## Getting started

Check prerequisites below ...

Export your aws credentials first like:
```
export AWS_ACCESS_KEY=xxxxx
export AWS_SECRET_KEY=xxx
export AWS_SESSION_TOKEN=xxxxxx
```
Normally this can be done with your favourite aws login tool (like [saml2aws](https://github.com/Versent/saml2aws)).

Now start your metadata service like:
```
pipenv run bin/server-macosx
``` 

This will try to redirect any requests to 169.254.169.254 to this small service.


## Prerequisites

This is intended and tests to work on current MacOSX (Mojave) only. It will definitely not work on MacOSX prior to 10.7 (firewalling is different).

You need additionally:
  * [pipenv](https://github.com/pypa/pipenv)

You need credentials to the desired aws account/role.

Onetime install dependencies (python):
``` 
git clone https://github.com/h1f1x/aws-simple-mock-metadata
cd aws-simple-mock-metadata
pipenv install
```

## Related Projects
  If you need more features you can try this one:
  * https://github.com/dump247/aws-mock-metadata
  * https://github.com/james-kelly/aws-metadata - another simple one, but not working with current MacOSX

## Further readings and projects
  * https://murusfirewall.com/Documentation/OS%20X%20PF%20Manual.pdf
  * https://github.com/Versent/saml2aws
  * https://bottlepy.org/docs/0.12/

Thanks [Cory Thomas](https://github.com/dump247/aws-mock-metadata) for the firewall rulings.
