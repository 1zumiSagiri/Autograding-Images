# Autograding Images

This repository contains Dockerfiles for autograding images used by Autolab and DevU.

## Using an image in Autolab

In the `Autograder Settings > VM Image` field, enter the name of the Dockerfile without the `Dockerfile_` prefix. E.g., to use Dockerfile_autograding_image on Autolab, enter `autograding_image`.

## Creating a new image

Instructors should read UB CSE's [Autolab Public Documentation](https://github.com/UB-CSE-IT/Autolab-Public-Documentation) to learn how to create a new autograding image. Then, create a Dockerfile that meets our requirements for standardization.

### Author label

Your Dockerfile must contain an author label at the top (as the first Dockerfile instruction). This is a [standard annotation](https://github.com/opencontainers/image-spec/blob/main/annotations.md) developed by the [Open Containers Initiative](https://opencontainers.org/). Multiple values can be separated by commas. E.g., `Alice Smith, Bob Jones`. You may optionally include email addresses in angle brackets after the name. E.g., `Alice Smith <alice@example.com>`. If you don't want to publish your real name, you may use your GitHub username.

```Dockerfile
LABEL org.opencontainers.image.authors="Alice Smith"
```

### File name

- Name your Dockerfile in the following format: `Dockerfile_cse_123`
  - If there are duplicates, a short suffix may be added after an underscore. E.g., `Dockerfile_cse_123_python`
  - Cross-listed courses should use the lowest course number. E.g., `Dockerfile_cse_486`
- Only use letters, numbers, and underscores
- All characters must be lowercase, except for the "D" in Dockerfile, which must be uppercase

### Create a pull request

- Create a fork of this repository
- Place your Dockerfile in the `dockerfiles` directory
- Create a pull request
- Contact CSE Consult requesting a review

Once approved and deployed, images will be available in Autolab without the `Dockerfile_` prefix. E.g., `cse_123`.

## Updating an existing image

As multiple instructors may rely on the same image, it's important to avoid breaking changes during a semester. One of the labeled authors of an image must approve any changes while classes are in session.

To update an image, create a pull request with the changes to the Dockerfile and contact CSE Consult requesting a review.

If you are not a labeled author, and classes are in session, a labeled author must also approve the pull request before it will be accepted.

Teaching assistants will need a primary instructor's approval to edit (or create) Dockerfiles.

Exceptions will be made if the labeled authors are unavailable (e.g., retired/graduated).

## Archiving images

After an image has not been used by any course on Autolab for a full year (365 days), it is eligible for archival. Archived images will be moved into a separate directory and removed from Autolab. If an archived image is needed again, it can be restored. After an image has been archived for a full year, it may be deleted (it will still be in the Git history).

## Deploying images

System administrators can use [Tangoctl](https://github.com/NicholasMy/tangoctl) to easily build and deploy these images across the Tango worker fleet.
