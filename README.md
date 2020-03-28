# Structured Data Linter
Extract and validate embedded RDF markup in HTML and other formats.

## DESCRIPTION
The Structured Data Linter digests structured data, in the form of HTML marked-up
with [RDFa][], [JSON-LD][], or [Microdata][], or other RDF technologies supported in
[Linked Data][linkeddata].

The linter is part of the [structured-data.org](http://structured-data.org/),
and runs at [linter.structured-data.org](http://linter.structured-data.org/)

* Includes [N-Triples][] support using [RDF.rb][].
* Includes [RDF/XML][] support using the [RDF::RDFXML][] gem.
* Includes [Turtle][] and [Notation3][] support using the [RDF::N3][] gem.
* Includes [RDFa][] support using the [RDF::RDFa][] gem.
* Includes [RDF/JSON][] support using the [RDF::JSON][] gem.
* Includes [TriX][] support using the [RDF::TriX][] gem.
* Includes [Microdata][] support using the [RDF::Microdata][] gem.
* Includes [JSON-LD][] support using the [JSON::LD][] gem.

Output is expressed as HTML+RDFa in a _Snippet_ format.

### Running locally
To run locally, do a `bundle install` to load required dependencies. Then run with `foreman` or `rackup`:

    foreman start

or

    rackup

### Schema.org examples
To update the examples from schema.org, run `rake schema:examples`. Warnings for these examples can be generated into {file:etc/schema-warnings.txt} by running `rake schema:warnings`; remember to run `bundle install` first.

### Code layout
This application is represented as a [Sinatra][] application implemented in [Ruby][].

    assets                -- Assets for web application
    config.ru             -- [Rack][] configuration file, to start application
    lib
      rdf
        linter
          parser.rb         -- Parse and transform input to RDFa.
          rdfa_template.rb  -- RDFa output templates in [Haml][]
          snippets          -- Snippet templates
          views             -- Templates for view generation in [Erubis][]
          writer.rb         -- Sub-class of [RDFa][] writer for generating snippet output.
        linter.rb         -- Controller defining HTTP endpoints
    spec                  -- Tests

## Dependencies
* [Haml](http://rubygems.org/gems/haml) (>= 4.0.0)
* [Erubis](http://rubygems.org/gems/erubis) (>= 2.7)
* [RDF.rb](http://rubygems.org/gems/rdf) (>= 1.0)
* [Linked Data](http://rubygems.org/gems/linkeddata) (>= 1.0)
* [Linked Data for Rack](http://rubygems.org/gems/rack-linkeddata) (>= 1.0)
* [Linked Data for Sinatra](http://rubygems.org/gems/sinatra-linkeddata) (>= 1.0)
* [Nokogiri](http://rubygems.org/gems/nokogiri) (>= 1.5.9)
* [RDF::JSON](http://rubygems.org/gems/rdf-json) (>= 1.0)
* [RDF::Microdata](http://rubygems.org/gems/rdf-microdata) (>= 1.0)
* [RDF::N3](http://rubygems.org/gems/rdf-n3) (>= 1.0)
* [RDF::RDFa](http://rubygems.org/gems/rdf-rdfa) (>= 1.0)
* [RDF::RDFXML](http://rubygems.org/gems/rdf-rdfxml) (>= 1.0)
* [RDF::TriX](http://rubygems.org/gems/rdf-trix) (>= 1.0)
* [JSON::LD](http://rubygems.org/gems/json-ld) (>= 1.0)

## AUTHORS
* [Gregg Kellogg](http://github.com/ruby-rdf) - <http://kellogg-assoc.com/>
* Stéphane Corlosquet

## Setup notes
* public/.htaccess
* Bundle installed using:

    bundle install --path vendor/bundler

* Start the server with:

    bundle exec shotgun -p 3000 config.ru

## FEEDBACK

* http://groups.google.com/group/structured-data-dev
* https://github.com/structured-data/linter/issues

## Contributing
* Do your best to adhere to the existing coding conventions and idioms.
* Don't use hard tabs, and don't leave trailing whitespace on any line.
* Do document every method you add using [YARD][] annotations. Read the
  [tutorial][YARD-GS] or just look at the existing code for examples.
* Don't touch the `.gemspec`, `VERSION` or `AUTHORS` files. If you need to
  change them, do so on your private branch only.
* Do feel free to add yourself to the `CREDITS` file and the corresponding
  list in the the `README`. Alphabetical order applies.
* Do note that in order for us to merge any non-trivial changes (as a rule
  of thumb, additions larger than about 15 lines of code), we need an
  explicit [public domain dedication][PDD] on record from you.

## License
This is free and unencumbered public domain software. For more information,
see <http://unlicense.org/> or the accompanying {file:UNLICENSE} file.

[JSON-LD]:        http://www.w3.org/TR/2013/CR-json-ld-20130910/
[Microdata]:      http://www.w3.org/TR/microdata-rdf/
[N-Triples]:      http://en.wikipedia.org/wiki/N-Triples
[Notation3]:      http://en.wikipedia.org/wiki/Notation3
[RDF/JSON]:       http://n2.talis.com/wiki/RDF_JSON_Specification
[RDF/XML]:        http://www.w3.org/TR/rdf-syntax-grammar/
[RDFa]:           http://en.wikipedia.org/wiki/RDFa
[TriX]:           http://en.wikipedia.org/wiki/TriX_(syntax)
[Turtle]:         http://en.wikipedia.org/wiki/Turtle_(syntax)
[Sinatra]:        http://www.sinatrarb.com/
[Ruby]:           http://www.ruby-lang.org/en/
[RDF.rb]:         http://rubygems.org/gems/rdf
[Linked Data]:    http://rubygems.org/gems/linkeddata
[RDF::Microdata]: http://rubygems.org/gems/rdf-microdata
[RDF::N3]:        http://rubygems.org/gems/rdf-n3
[RDF::RDFa]:      http://rubygems.org/gems/rdf-rdfa
[RDF::RDFXML]:    http://rubygems.org/gems/rdf-rdfxml
[RDF::TriX]:      http://rubygems.org/gems/rdf-trix
[JSON::LD]:       http://rubygems.org/gems/json-ld
[Haml]:           http://haml-lang.com/
[Erubis]:         http://www.kuwata-lab.com/erubis/
[Rack]:           https://github.com/rack/rack/wiki# lastlinter

Launch ec2 instance machine AMI: 

Amazon Linux AMI 2018.03.0 (HVM), SSD Volume Type - ami-09a5b0b7edf08843d

sudo yum install -y curl gpg gcc gcc-c++ make
sudo gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
curl -sSL https://get.rvm.io | sudo bash -s stable
sudo usermod -a -G rvm `whoami`
if sudo grep -q secure_path /etc/sudoers; then sudo sh -c "echo export rvmsudo_secure_path=1 >> /etc/profile.d/rvm_secure_path.sh" && echo Environment variable installed; fi
reconnect
check with rvm --version
rvm install ruby-2.5.7
ruby --version
gem install bundler --no-rdoc --no-ri
curl --silent --location https://rpm.nodesource.com/setup_8.x | sudo bash -
sudo yum install -y nodejs
gem install rails
rails --version
sudo yum install git
git clone https://github.com/ankitadhandha/lastlinter.git
enter username password
sudo yum install docker
sudo service docker restart
sudo docker run --name sdlcontainer -it -v $PWD:/var/task -w /var/task lambci/lambda:build-ruby2.5 /bin/bash
if required make changes in template.yaml file.
bundle install --deployment
look at this https://stackoverflow.com/questions/51409209/dockerfile-copy-files-from-amazon-s3-or-another-source-that-needs-credentials/55537106#55537106
and create role and attach to EC2 instance
du -sh
rm -rf vendor/bundle/ruby/2.5.0/cache
du -sh
355 M
find -type d -name ".git"
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-500d5d931fb0/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/sxp.rb-a6201a87d980/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/json-ld-3eb7618536b0/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/json-ld-preloaded-b4a16b53a488/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/jsonlint-f817a0b40174/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-xsd-276267e926a9/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-aggregate-repo-3eab6256caf1/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/sparql-client-8b2723ff9503/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/sparql-2d2905435bf8/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/ld-patch-123066e78d9b/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-isomorphic-2296d9b85edb/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-json-f201f2e3bb9a/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-microdata-68a40811b1a9/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-n3-015ce184efe3/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-normalize-d7576ee0e9f1/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-rdfa-74b60100bc6a/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-rdfxml-5d54dc31182d/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-vocab-7045061c8659/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-reasoner-dc33ae391715/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-tabular-a0f61ab12f85/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-turtle-6d0fafc31f4c/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-trig-daf7ec596ea8/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-trix-14f596807fd7/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/shex-0e03d9f48908/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/linkeddata-eb3167191b95/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rack-linkeddata-0209c3b0110e/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/sinatra-linkeddata-074d7e08ec93/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-do-0c99dea75993/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-spec-484d46c7a474/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rest-client-components-236ac31ed1a0/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-96fc834d6b23/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/rdf-vocab-8858ef97ebf5/.git
rm -rf ./vendor/bundle/ruby/2.5.0/bundler/gems/json-ld-60970aa39157/.git
du -sh
316M
cd vendor/bundle/ruby/2.5.0/bundler/gems
du -a --max-depth=1 | sort -n
rm -rf json-ld-60970aa39157/example-files/
du -sh /var/task
290M
rm -rf sparql-2d2905435bf8/examples
du -sh /var/task
290M
cd /var/task
rm -rf /var/task/vendor/bundle/ruby/2.5.0/bundler/gems/rdf-normalize-d7576ee0e9f1/spec/w3c-normalization
rm -rf /var/task/vendor/bundle/ruby/2.5.0/bundler/gems/rdf-n3-015ce184efe3/spec/swap
rm -rf /var/task/vendor/bundle/ruby/2.5.0/bundler/gems/rdf-n3-015ce184efe3/spec/w3c-n3
create bucket sdl-lambda on s3 or create using aws cli
create assets and its subfolders in sdl-lambda bucket.
aws cloudformation delete-stack --stack-name sdlv2
aws cloudformation package --template-file template.yaml --output-template-file serverless-output.yaml --s3-bucket sdl-lambda
aws cloudformation deploy --template-file serverless-output.yaml --stack-name sdlv2 --capabilities CAPABILITY_IAM
Make changes in application.js file to have new API gateway endpoint for post and get request.




