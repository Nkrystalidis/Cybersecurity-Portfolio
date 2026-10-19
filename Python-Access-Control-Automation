# Automated Access Control List (ACL) IP Updater
# Scenario: Healthcare subnetwork restricted access management


def update_file(import_file, remove_list):
  """Reads an IP allow list file, removes unauthorized IP addresses

  specified in the remove_list, and rewrites the updated file.
  """
  # Step 1: Open the file and read its initial contents into a string
  with open(import_file, "r") as file:
    ip_addresses = file.read()

  # Step 2: Convert the string of IP addresses into a list for manipulation
  ip_addresses = ip_addresses.split()

  # Step 3: Iterate through the list and remove revoked IP addresses
  for element in remove_list:
    if element in ip_addresses:
      ip_addresses.remove(element)

  # Step 4: Convert the list back into a formatted string
  ip_addresses = "\n".join(ip_addresses)

  # Step 5: Rewrite the original file with the revised allow list
  with open(import_file, "w") as file:
    file.write(ip_addresses)


# Define target file and revoked employee IP addresses
allow_list_file = "allow_list.txt"
revoked_ips = ["192.168.25.60", "192.168.140.81", "192.168.203.198"]

# Execute the update algorithm
update_file(allow_list_file, revoked_ips)

# Verify the updated file contents
with open(allow_list_file, "r") as file:
  updated_text = file.read()

print(updated_text)
