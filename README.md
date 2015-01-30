Form Queue
==========

Form Queue intercepts form submissions and queues them rather than process them
upon submission. Processing is delegated to workers processing the queue.


Proof of concept
----------------

The proof of concept is hard-coded to use Webform as an example.

 - Create a webform with Webform module.
 - Submit data. Try to view results. Note: You don't see any results. The form
   submission is waiting in a queue to be processed.
 - Review items in the queue: `drush queue-list`
 - Process next item in the queue: `drush queue-run form_queue_submissions`
   (For real life use, you'd want this command running continuously in the
   background. For enterprise applications with high volumes of
   submissions use the aws_sqs module to replace Drupal's default MySQL queue
   with AWS's Simple Queue Service.)
 - Review webform results again. You should see your submission now.

