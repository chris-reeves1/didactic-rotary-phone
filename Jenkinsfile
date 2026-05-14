pipeline{
    
}


/*

parameters{ booleanParam(
    name: 'USE_SLIM_IMAGE'
    default: false
    description: ""
    )}

environemnt{
    dockerhub
    image_tag
    original_image
    slim_image
    nginx_image
    dockerhub_repo
}

fs scan

clean up/prep

unit test

build original images

build slim image:
    when { expression { return params.USE_SLIM_IMAGE } }

select slim/original:
    script:
        if..param.USE_SLIM_IMAGE
            then..
        else ..

collect metaData:
    inspect
    image ls
    history 
        post always archive

image_size_gate
    200 + == unstable()

image security scan

generate SBOM

quality gate

run containers (if needed)

smoke test
    if fail print all logs

login tag and push to dockerhub
    example:
    env {DOCKERHUB_CREDENTIALS = credentials('dockerhub_creds')}

    echo "$DOCKERHUB_CREDENTIALS_PSW" | docker login -u "$DOCKERHUB_CREDENTIALS_USR" --password-stdin

pipeline post actions:
    echo? 



*/