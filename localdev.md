---
layout: default
---

Developing your GitHub page locally allows you can preview your changes before pushing it to the live site. The changes are also shown immediately on your computer (where as changes to the live site could take 1-2 minutes to update). Below are instructions to get it to work on **KTBYTE Virtual Machines**, which runs Linux, but Jekyll has install guide for [Mac](https://jekyllrb.com/docs/installation/macos/) (Official) and [Windows](https://jekyllrb.com/docs/installation/windows/) (Unofficial) as well. 

1. open the __terminal__ and install the needed software:


        sudo apt update
        sudo apt install ruby-full build-essential zlib1g-dev -y
        gem install jekyll bundler
        gem install jekyll-theme-minimal
        
        echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
        echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
        echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
        source ~/.bashrc
        gem install jekyll bundler
        gem install jekyll-theme-minimal

    If you used a different jekyll theme, make sure to also the corresponding gem by doing `gem install jekyll-theme-<theme-name`.

2. Clone your repository. Go to your project's GitHub page and click the green "Code" button and copy the clone URL. Then do the following in the __terminal__:

        mkdir -p ~/sync/workspace
        cd ~/sync/workspace
        git clone <url>
        cd <url>

3. Run your page locally with the following:

       jekyll serve --incremental

    You should now see your web site running at [http://localhots:4000](http://localhots:4000). If the URL loads but you see a file listing instead of your web page. Make sure that your __index.md__ file has the following "front matter" at the top:

        ---
        layout: default
        ---

4. Open up the project in Visual Studio Code and make changes as needed.


5. When you are ready to publish, add a public key to push to your repository. Generate a SSH key for your github account, by running the following in your terminal:

        ssh-keygen

    (Press enter for any prompts to go with default settings)

    Get your public key with the following command:

        cat ~/.ssh/id_rsa.pub

    Go to the [Github Key Settings](https://github.com/settings/keys) page to import your public key.

6. Push changes to live site. When you are happy with your changes, do the following to push your changes to live site:

        git add -A 
        git commit -m "a good commit message"
        git push

    Wait for the site to go live!
