Nodetime on OpenShift
======================
This git repository helps you to setup Nodetime and to showcases a working configuration of the Nodetime agent.


Running on OpenShift
----------------------------

Create a Nodetime account at https://nodetime.com/signup.

Create an account at http://openshift.redhat.com/ and set up you local machine with the client tools.

Create a node-0.6 application (you can call your application whatever you want)
<pre>
  rhc app create nodetime node-0.6
</pre>

Add this upstream Nodetime Quickstart repo
<pre>
  cd nodetime
  git remote add upstream -m master git://github.com/openshift/nodetime-openshift-quickstart.git
  git pull -s recursive -X theirs upstream master
</pre>


###Configuration###
Configure <strong>server.js</strong> file with your information:

<pre>
  require('nodetime').profile({
    accountKey: 'my_account_key',
    appName: 'My OpenShift Node.js App'
  });
</pre>

<code>accountKey</code> - You can find your account key on the https://nodetime.com/account page.
<code>appName</code> - The name under which your application's web console will be available in your Nodetime account.

For advanced configuration options please see API documentation at http://docs.nodetime.com/#agent-api.


Then push the repo
<pre>
  git add .
  git commit -m "my first commmit"
  git push
</pre>

That's it, you can now checkout your application at:
<pre>
  http://nodetimeshowcase-$yournamespace.rhcloud.com
</pre>

And visit Nodetime's web console from https://nodetime.com/apps page.

For more details about the Nodetime service please visit the documentation pages at http://docs.nodetime.com or contact our Support Team at http://support.nodetime.com.
